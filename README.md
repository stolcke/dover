# dover
DOVER - an algorithm for combining diarization hypotheses
=========================================================

FILES
-----

scripts/dover                   The top-level script  
scripts/dover-sort-rttms        Helper script to sort input rttms by average DER  
scripts/dover-speaker-voting    Helper script to tally votes after label mapping  
scripts/md-eval.pl              NIST DER scoring tool  

scripts/diar-score-report       helper script for DER score extraction  
scripts/stat-dist               helper script for computing score statistics  

doc/                            DOVER paper and other documentation  

example1/                       The example from the paper  
example2/                       Actual sample run from a Denmark experiment  

REQUIREMENTS
------------

Linux or Cygwin environment.  To run in the Windows 10 subsystem for Linux, use

                bash -c '.../scripts/dover ...'

gawk and perl need to be installed.

USAGE
-----

        dover [-option ...] [w1] rttm1 [w2] rttm2 ... > combined.rttm

where rttm1, rttm2, ... are the diarization outputs to be combined,
and w1, w2, are optional weights for the respective inputs.

The outputs have to pertain to a single audio file that is assumed to be the same
for all inputs.  Therefore, the waveform name and channel fields in the inputs
are ignored.

OPTIONS
-------

    -name NAME
        Use NAME as the waveform name in the output rttm file.

    -tmpdir DIR
        Sets the directory where working files are kept.  Default is "DOVER".

    -split_ties
        Split ties among labels for an output segment in time, e.g., if there is
        tie among speakers A, B, C then the segment will be split into 1/3 A, 1/3 B
        and 1/3 C. The labels are permuted to attempt to minimize speaker changes
        with adjacent segments.

    -rotate
        Rotate the label alignment anchor among all the inputs, and combine the
        resulting output again, using DOVER with equal weights

    -rotate_split_ties
        Like -rotate, with -split_ties in the final combination step.

    -sort_by_der
        Compute the average DER between each input and all the other inputs, and
        process them in order of smallest first.  In particular, the centroid
        hypothesis will be the anchor for label alignment.

    -rank_weighted S
        In conjunction with -sort_by_der, weight the inputs according to the ranks,
        by (1/rank)^S.  S determines the steepness of the weight fall-off, and is
        typically 0.1.

CITATION
--------

Any work making use of, or referencing, the DOVER code or algorithm should cite

  A. Stolcke & T. Yoshioka, DOVER: A Method for Combining Diarization Outputs, 
  Proc. IEEE Automatic Speech Recognition and Understanding Workshop, Singapore, Dec. 2019,
  pp. 757-763. http://arxiv.org/abs/1909.08090
