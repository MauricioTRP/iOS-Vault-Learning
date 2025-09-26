Subscripts are shortcuts for accessing member elements of a collection, list or sequence.
This can be defined on Classes, Structs and Enums (they define types)

For instance `Array` use subscript notation, and looks like this:

```swift
Array[index]
myDictionary[key]
```

You can define subscript overload for different types.

Here's an example:

```swift
struct TimesTable {
	let multiplier: Int
	subscript(index: Int) -> Int {
		return multiplier * index
	}
}

let threeTimesTable = TimesTable(multiplier: 3)
print("Six times three is \(threeTimesTable[6])")
// prints "Six times three is 18"
```

## Usage
What subscript means depends on the context.
They're typically used as shortcut for accessing member elements in a collection, list or sequence. But you can implement in a way that make sense in the context

As example dictionaries implement subscript to get/set stored information at that key

```swift
var numberOfWheels = ["car": 4, "truck": 8, "bike": 2]
numberOfWheels["monocycle"] = 2 
```

## Definition

Any kind of subscript you want to use in your types, could be defined (as far as I know) in two ways:

1. Instance subscripts:

```swift
type YourType {
	// Some definitions and members
	subscript(yourInputValues...) {
		get {
			// How you should get the values
		}
		set {
			// How you should set the values
		}
	}
}

```

This lets any instance of `YourType` use the subscript notation

```swift
let instaceOfYourType = YourType()

instanceOfYourType[/* some way to get or set accordingly to definitions */]
```

2. Type Subscripts
```swift
// TODO
```


