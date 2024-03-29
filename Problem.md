**File Reduce**

Consider a text file that has millions of records and has the following
properties:

1. Each line has one record on it.

2. Each record has comma separated values in the following format :-

     type, symbol, price, quantity, expirydate, strikeprice, amendtime, id, parentid

3. A record in the file can be uniquely identified by the "id".

4. The type field can have two values T and P, where T represents the
parent and P represents the child respectively.

5. A record R1 is the child of another record R2, if the type of R1 is P
and the parentid of R1 equals the id of R2.


Sample file:

	T,ICICIBANK,1000,100,20121210,120,20121209103030,1234,0

	T,AXISBANK,1000,100,20121210,120,20121209103031,1235,0

	T,SBIBANK,1000,100,20121210,120,20121209103032,1236,0

	P,ICICIBANK,1100,100,20121210,120,20121209103030,1237,1234

	P,AXISBANK,1000,100,20121210,120,20121209103031,1238,1235

	T,ICICIBANK,1000,100,20121210,120,20121209103035,1239,0

	T,.CITIBANK,1000,101,20121210,120,20121209103036,1240,0

	P,ICICIBANK,1100,100,20121210,120,20121209103030,1241,1234

	P,ICICIBANK,1100,100,20121210,120,20121209103035,1242,1239

type,    symbol,       price,  quantity, expirydate, strikeprice, amendtime,    id, parentid

T	ICICIBANK	1000	100	20121210	120	2.01212E+13	1234	0
T	AXISBANK	1000	100	20121210	120	2.01212E+13	1235	0
T	SBIBANK		1000	100	20121210	120	2.01212E+13	1236	0
P	ICICIBANK	1100	100	20121210	120	2.01212E+13	1237	1234
P	AXISBANK	1000	100	20121210	120	2.01212E+13	1238	1235
T	ICICIBANK	1000	100	20121210	120	2.01212E+13	1239	0
T	.CITIBANK	1000	101	20121210	120	2.01212E+13	1240	0
P	ICICIBANK	1100	100	20121210	120	2.01212E+13	1241	1234
P	ICICIBANK	1100	100	20121210	120	2.01212E+13	1242	1239


Write an optimal program that takes a file and an integer X as command
line arguments and splits the input file into maximum number of smaller
files such that each smaller file contains a minimum of X number of records
with the condition that all the children of a parent record should be in
the same file as the parent record. Each smaller file should be named as
output_<n>.txt where value n is  1, 2, 3 ... N (maximum number of files
possibles)

For e.g. if the sample file above is split into files containing minimum
two rows each, then records -

	T,ICICIBANK,1000,100,20121210,120,20121209103030,1234,0

	P,ICICIBANK,1100,100,20121210,120,20121209103030,1237,1234

	P,ICICIBANK,1100,100,20121210,120,20121209103030,1241,1234
	
should be in one file.
