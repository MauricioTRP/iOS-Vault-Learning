Every language have its own basic data types which works as basic building blocks.

In Swift we have:
## Integers
The most simple numerical types in this language, they have signed and unsigned variants and the size could depend on the platform:

Let's first check a simple example of this numbers represented by [two's complement][1]

|Binary (8-bit)|Decimal Value|Notes|
|---|---|---|
|`0000 0000`|0|Zero|
|`0000 0001`|+1|Positive|
|`0000 0010`|+2||
|...|...|Continues upward|
|`0111 1111`|+127|Maximum positive|
|`1000 0000`|-128|Minimum negative|
|`1000 0001`|-127||
|`1000 0010`|-126||
|...|...|Continues upward|
|`1111 1110`|-2||
|`1111 1111`|-1|Maximum negative (closest to 0)|

If you need to get the negative of a number, flip the bits and add 1:


```markdown
+127  = 0111 1111  
Flip  = 1000 0000  
+1    = 0000 0001  
----------------  
-127  = 1000 0001

```

That way you can represent sum of numbers whether they are positive or negatives.
If you want to add numbers, just have to move a carry (we'll see that in class)

Other types of `Int` in Swift

| Type     | Size                | Range                     | Simple Description                                                                                                             |
| -------- | ------------------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `Int`    | Platform Specific   | Platform Specific         | Integer with sign, the size is platform specific `Int32` or `Int64` depending on native word size                              |
| `Int16`  | 16 bit              | $-2^{15}$ to $2^{15} - 1$ | The "one element less" if taken by zero, and 2 to the power of 15 is because the 16th bit is used by sign                      |
| `Int32`  | 32 bit              | $-2^{31}$ to $2^{31} - 1$ | The analogy is the same, 32th bit is used by sign, and in the upper boundary we have 1 element less due to zero representation |
| `Int64`  | 64 bit              | $2^{63}$ to $2^{63} - 1$  | .... same explanation                                                                                                          |
| `UInt32` | Depends on platform | $0$ to $2^{32}$           |                                                                                                                                |
| `UInt64` | Depends on platform | $0$ to $2^{64}$           |                                                                                                                                |

```swift
let number: UInt32 = 500
```
## Floats and Doubles

This numbers differ on how they are represented in Memory, that's why you must cast the numbers if you need to do computation with both types.

Normally they're based on standards like [IEEE 754][2]
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d2/Float_example.svg/590px-Float_example.svg.png)](https://en.wikipedia.org/wiki/File:Float_example.svg)
which leaves space for fraction numbers named mantisa and the "hole" numbers or exponent, and a bit for sign.

```swift
let myDouble: Double = 3.5
let myFloat: Float = 3.5f
```

## Booleans
Values that serves to evaluate "truthiness" they either be `true`or `false`

```swift
let myTrue: Bool = true
let myFalse: Bool = false
```

## Characters and Strings

Character represents a single character for example `A` `z` values, and strings represents a sequence of characters: `My String value`

```swift
let myChar: Character = "A"
let myString: String = "My String"
```



[1]: https://en.wikipedia.org/wiki/Two%27s_complement
[2]: https://en.wikipedia.org/wiki/IEEE_754