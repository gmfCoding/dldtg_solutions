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



| S | A | Z0| Z1|
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 0 |
| 1 | 1 | 0 | 1 |


| S | A | Z0| Z1|   |
|---|---|---|---|---|
| 0 | 1 | 1 | 0 | S̅ ∧ A |
| 1 | 1 | 0 | 1 | S ∧ A |

Plot the minterms on the k-map

### K-Map Z0
|S \ A|   |0 |1 
|------|--|---|---|
| 0    |\|| - | 1 |
| 1    |\|| - | - |


### K-Map Z1
|S \ A|   |0 |1 
|------|--|---|---|
| 0    |\|| - | - |
| 1    |\|| - | 1 |


| Result |
|-------------|
| AS̅ ∨ SB |

### Apply DML:
#### ∼(X & Y) = ∼X ∣ ∼Y
#### ∼(X ∣ Y) = ∼X & ∼Y
#### X&Y = X&(~X+Y)

~S & A


~~(A & ∼(A & S))

∼(∼(~S & A))

S ∣ ∼A

S + (~S∼A)

# Original
Z0 = ∼(∼S & ∼(~S∼A))
Z1 = ~~(S & A)


~S & A
S & A


# More per individual less overall




# Better
Z0 = ~~(A & ∼(A & S))
Z1 = ~~(S & A)

DEF DEMUX12
  PORT IN A
  PORT IN S
  PORT OUT Z0
  PORT OUT Z1
  

  # FIRE: ∼(A & S)
  # WATER: ~(A & FIRE)
  NET FIRE
  NET WATER

  # ∼(A & S)
  INST N1 NAND A S FIRE

  # ~(A & ∼(A & S))
  INST N2 NAND A FIRE WATER

  # A & FIRE (fire)
  INST N3 NOT WATER Z0

  # A & S
  INST N4 NOT FIRE Z1
ENDDEF
