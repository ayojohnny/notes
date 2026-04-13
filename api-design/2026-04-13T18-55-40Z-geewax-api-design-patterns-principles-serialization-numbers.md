# API Design | Principles - Serialization - Numbers

Numbers:
- enable storage of numerical values (integer or floating-point/decimals)
- use when wanting to perform arithmetic calculations
- avoid using as numeric **identifiers** of resources

Numbers should be used for their numeric or arithmetic benefit (i.e. the ability
to operate in an arithmatic way - subtract, add, divide, etc.) and not soley because
they are numeric characters (that's what strings are for!).

Prime example, it doens't make sense to add `numeric identifiers`... since the 
semantic meaning would be pretty useless compared to adding `priceUsd` for all items.

When using numeric fields, the following should be considered:
1. upper bound (max value)
2. lower bound (min value)
3. zero value (default value)



Upper & Lower Bounds:

Worring about the upper and lower bounds of numeric input is important since progra-
mming languages handle numbers differently. There is possiblity for languages not
to be able to properly parse (or even truncate) some data if upper and lower bounds
are not considered.

Common practice is to rely on `64-bit integer` types for whole numbers.

