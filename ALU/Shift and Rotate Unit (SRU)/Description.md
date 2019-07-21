# Shift and Rotate Unit (SRU)

The SRU is responsible for these operations:

- `SHRA` (Shift Right Arithmetic)

- `SHRL` (Shift Right Logical)

- `ROTR` (Rotate Right)

The inputs and outputs are:

- `I0:I7` (Input byte)

- `S0:S2` (Shift amount)

- `R` (High = Rotate, Low = Shift)

- `A` (High = Arithmetic Shift, Low = Logical Shift)

- `L` (High = Shift/Rotate Left, Low = Shift/Rotate Right)

- `O0:O7` (Output byte)

Assumptions:

- If `R` is High, then `A` must be Low.

## Implementation

The SRU is implemented as a modified barrel shifter. It uses three rows of 2:1 multiplexers to shift the input 1, 2, or 4 places to the right. Rotate Right uses wrap-around connections enabled by `R`. Shift Right Arithmetic uses the `A` input, which copies the sign bit into all bits that would rotate into the MSB.


