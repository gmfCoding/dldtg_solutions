
Find SOURCE for given truth table using: 
http://alanclements.org/boolean_example_1.html


Source is derived from the sum of products of the truth-table
Which is simplifide using a kmap into the following:
### SOURCE
~(~(B & ~C) & ~(B & ~D) & ~(A& ~D) & ~(A & C))

#### TARGET
~(~(B & ~(C & D)) & ~(A & ~(D & ~(C & D))))


#### First Group Target
~(B & ~(C & D))

#### Second Group Target
~(A & ~(D & ~(C & D)))

## <u>First Group</u>

~(B & ~C)
~(B & ~D)


#### Apply DeMorgans law
#### ∼(X & Y) = ∼X ∣ ∼Y
#### ∼(X ∣ Y) = ∼X & ∼Y

(~B + ~~C)
(~B + ~~D) 

#### Double negatives cancel out
#### ~~X = X

(~B + C)
(~B + D) 

#### Apply distributive law
#### X + YZ = (X + Y) & (X + Z)
~B + CD

#### Apply DeMorgans Law Again
~(B & ~(C & D))


∼(B & ∼(C & D))

## <u>Second Group</u>

~(A & ~D)
~(A & C)

#### Apply DeMorgans Law 
(~A + ~~D)
(~A + ~C)

#### negatives cancels

(~A + D)
(~A + ~C)

#### Apply distributive
#### X + YZ = (X + Y) & (X + Z)
~A + (D & ~C)

#### Apply De Morgans Law
#### ∼(X & Y) = ∼X ∣ ∼Y
#### ∼(X ∣ Y) = ∼X & ∼Y

~A + (D & ~C)

#### Apply Expansion
#### X&Y = X&(~X+Y) with X = D Y = ~C

~A + (D & (~D + ~C))

#### Apply commutative law

~A + (D & (~C + ~D))

#### Apply DML

~A + (D & ~(D & C))

#### Apply double negation

~A + ~~(D & ~(D & C))

#### Apply DML

~(A & ~(D & ~(C & D)))



#### SOURCE
~(FIRST_GROUP & SECOND_GROUP)
#### First Group Target
~(~(B & ~(C & D)) & ~(A & ~(D & ~(C & D))))


~( & )

~(B & )

~(A & )

~(D & )

~(C & D)
