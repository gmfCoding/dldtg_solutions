DEF DEMUX21
  PORT IN A
  PORT IN S
  PORT OUT Z0
  PORT OUT Z1
  
  NET !S
  NET !A
  NET !SA

  INST N1 NOT S !S
  INST N2 NOT A !A

  INST N3 NAND !S !A !SA
  INST N4 NAND !S !SA Z0
  INST N5 AND S A Z1

ENDDEF


A is I0
B IS I1



| S1|S0 | A | Z0| Z1| Z2| Z3|
|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 1 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 | 1 | 0 | 0 |
| 1 | 0 | 0 | 0 | 0 | 1 | 0 |
| 1 | 1 | 1 | 0 | 0 | 0 | 1 |


| S1| S0| A | Z0| Z1| Z2| Z3|   |
|---|---|---|---|---|---|---|---|
| 0 | 0 | 1 | 1 | 0 | 0 | 0 | !S1 & !S0 & A |
| 0 | 1 | 1 | 0 | 1 | 0 | 0 | !S1 & S0 & A |
| 1 | 0 | 1 | 0 | 0 | 1 | 0 | S1 & !S0 & A |
| 1 | 1 | 1 | 0 | 0 | 0 | 1 | S1 & S0 & A |

Plot the minterms on the k-map


DEF DEMUX14
  PORT IN A
  PORT IN S<1:0>
  
  PORT OUT Z0
  PORT OUT Z1
  PORT OUT Z2
  PORT OUT Z3
  
  NET MXLO
  NET MXHI
  
  INST DM1 DEMUX12 A S<1> MXLO MXHI
  INST DM2 DEMUX12 MXLO S<0> Z0 Z1
  INST DM3 DEMUX12 MXHI S<0> Z2 Z3
ENDDEF