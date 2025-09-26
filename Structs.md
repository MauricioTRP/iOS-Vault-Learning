Are the "goto" by default, share things in common with [[Classes]] like:

- Define properties to store values
- Define methods to provide functionality
- Define subscripts to provide access to their values using subscript syntax
- Define initializers to set up initial state
- Be extended to expand functionality
- Conform to [[Protocols|protocols]] to provide standard functionality

> [!Note]
> structs as well as classes are new types you are creating. That being said you must name then using `PascalCase` naming style, just like any other type in Swift `String`, `Int` or `Bool`

Here's an example of a struct definition:

```swift
struct XYPoint {
	var x: Int
	var y: Int
}
```

