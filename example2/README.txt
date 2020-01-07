DOVER applied to meeting diarization output using MFCC features
(ASRU paper, Table 2, row 1)

go.1.run-dover		runs DOVER 
go.2.score-dover	computes DER for all inputs and DOVER output

It should produce this output:

MISSED
	AVERAGE mean 11.524
	WORST mean 11.74
	BEST mean 11.42
	combined mean 11.36
FALARM
	AVERAGE mean 0.66
	WORST mean 0.62
	BEST mean 0.66
	combined mean 0.64
SPKERR
	AVERAGE mean 24.23
	WORST mean 34.56
	BEST mean 15.56
	combined mean 15
DER
	AVERAGE mean 36.39
	WORST mean 46.934
	BEST mean 27.594
	combined mean 26.984

