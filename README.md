# Optionals lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1

`var userName: String?`

Write 3 different ways of safely unwrapping and printing the value of `userName`.  If it is nil, print "No name".

- Method one: Check for nil and force unwrap

- Method two: Optional binding

- Method three: Nil coalescing

```swift
var userName: String?

// Check for nil and force unwrap
if userName != nil {
    print("Name:",userName!)
} else {
    print("No name entered")
}

// Optional Binding
if let name = userName {
    print("Name:", name)
} else {
    print("No name entered")
}

// Nil coalesing
let myname = userName ?? "No name entered"
```


## Question 2

Given optional string `backgroundColor`, write code that safely unwraps and prints it. If backgroundColor is nil, give it a value.

`var backgroundColor: String?`

```swift
var backgroundColor: String?
let color = backgroundColor ?? "Grey"
print(color)
```

## Question 3

Given an optional width and an optional height of a rectangle, write code that calculates and prints the area. Print an error message if either value is nil.

```swift
var width: Double?
var height: Double?

width = 10.00
height = 5.00

if let width = width, let height = height {
    print("The area is:", width * height)
} else {
    print("Error: Please provide a width and a height.")
}
```


## Question 4

Given the following optional variables `name`, `age` and `height`. Write code so that it prints `name`, `age` and `height` if they all have a value. If any are nil, print an error message. Try using optional binding.

```swift
var name: String?
var age: Int?
var height: Double?

name = "Phillip"
age = 26
height = 6.4

if let name = name, let age = age, let height = height {
    print("Name:", name)
    print("Age:", age)
    print("Height:", height)
} else {
    print("Error: Name, Height and Age must be initalized before we can continue.")
}

```


## Question 5

Given the variables `firstName`, `middleName` and `lastName`. Create a variable called `fullName` that is a nicely formatted string.

```swift
var firstName: String = "Johnny"
var middleName: String?
var lastName: String = "Stone"
var fullname: String

if let middlename = middleName {
    print("Name:",firstName,middlename,lastName)
} else {
    print("Name:",firstName,lastName)
}
```


## Question 6

Write code that adds 15 to `myIntString`, then prints the sum. Use the `Int()` constructor which returns an optional Int `(Int?)`.

`let myIntString = "35"`

```swift
let myIntString = "35"
var myInt: Int?

if var myInt = Int(myIntString) {
    myInt = myInt + 15
    print(myInt)
} else {
    print("Please use a valid integer.")
}
```


## Question 7

Given an optional tuple of optional Ints, write code to safely unwrap the tuple and calculate the sum of its contents that aren't nil.

```swift
var scores: (Int?, Int?, Int?)?

var testCaseOne: (Int?, Int?, Int?) = (4, nil, 7)
var testCaseTwo: (Int?, Int?, Int?) = (nil, nil, 9)
var testCaseThree: (Int?, Int?, Int?) = (5, 10, 24)

let arrayOfTestCases = [testCaseOne,testCaseTwo,testCaseThree]

var counter = 0
while counter < arrayOfTestCases.count{
    var sum = 0
    scores = arrayOfTestCases[counter]

    if let possibleScores = scores {
        let a = possibleScores.0 ?? 0
        let b = possibleScores.1 ?? 0
        let c = possibleScores.2 ?? 0
        sum = a + b + c
    }

    print("Test case \(counter + 1)'s sum is \(sum).")
    counter += 1
}
```


## Question 8

Safely unwrap `tuple` if there’s a non-nil tuple value and print it out.

```swift
var tuple: (Int, Int)?
if Bool.random() {
    tuple = (5, 3)
}

if let optionalTuple = tuple {
    print(optionalTuple)
} else {
    print("Error: your tuple need to be fully initalized.")
}
```


## Question 9

Write code that either doubles `myInt` and then prints it, or prints an error message if myInt is nil.

```swift
var myInt: Int?

if Bool.random() {
    myInt = 5
}

if let integer = myInt {
    print("myInt:", integer)
    print("myInt doubled:", integer * integer)
} else {
    print("Error: myInt is nil")
}
```


## Question 10

Write code that prints out the product of `myDouble` and `doubleTwo` or prints an error message if `myDouble` is nil.

```swift
var myDouble: Double?
let doubleTwo: Double = 5

if Bool.random() {
    myDouble = 12
}

if let double = myDouble {
    print("myDouble:",double)
    print("myDouble * doubleTwo:", double * doubleTwo)
} else {
    print("Error: myDouble is nil")
}
```


## Question 11

Determine if the variable contains a Boolean or nil value. If nil set the variable to false, else keep it true.

```swift
var isTheGreatest: Bool?

if Bool.random() {
    isTheGreatest = true
}

if let bool = isTheGreatest {
    print(bool)
} else {
    isTheGreatest = false
    print(isTheGreatest!)
}
```


## Question 12

Given the code below print the sum of each non-nil element in `myTuple`.

 ```swift
 var myTuple: (Int?, Int?, Int?, Int?)
 
 if Bool.random() {
     myTuple.0 = 5
     myTuple.2 = 14
 } else {
     myTuple.1 = 9
     myTuple.3 = 10
 }
 
 let a = myTuple.0 ?? 0
 let b = myTuple.1 ?? 0
 let c = myTuple.2 ?? 0
 let d = myTuple.3 ?? 0
 
 print(a+b+c+d)
```


## Question 13
Given the helper functions and code below, check to see if your `evolutionaryStone` is able to evolve your pokemon.  The table below shows the appropriate matches of pokemon to stone:

| Pokemon	   | Stone    |
| :--------: | :------: |
| Pikachu	   | Electric |
| Bulbasaur	 | Grass    |
| Charmander | Fire     |
| Squirtle	 | Water    |


```swift
// Helper Functions

func eStone() -> String {
let random = Int(arc4random_uniform(5))
switch random {
case 0:
return "Electric"
case 1:
return "Grass"
case 2:
return "Fire"
case 3:
return "Water"
default:
return "No Stone"
}
}

func starterPokemon() -> String {
let random = Int(arc4random_uniform(5))
    switch random {
    case 0:
        return "Pikachu"
    case 1:
        return "Bulbasaur"
    case 2:
        return "Charmander"
    case 3:
        return "Squirtle"
    default:
        return "Not a Pokemon"
    }
}

let pokemon: String?
var evolutionaryStone: String?
pokemon = starterPokemon()
evolutionaryStone = eStone()

let correctCombinations = [(pokemon: "Pikachu", eStone: "Electric"),(pokemon: "Bulbasaur", eStone: "Grass"),(pokemon: "Charmander", eStone: "Fire"),(pokemon: "Squirtle", eStone: "Water")]

var isMatch = false

if let pokemon = pokemon, let eStone = evolutionaryStone {
    print(pokemon,"&",eStone)
    for combo in correctCombinations where combo.pokemon == pokemon && combo.eStone == eStone {
        isMatch = true
        break
    }
    isMatch ? print(pokemon,"and",eStone,"is a match!") : print(pokemon,"and",eStone,"is not a match!")
} else {
    print("Error: Must provide a pokemon and evolutionary stone.")
}
```


## Question 14

Given an optional int `numberOfPeople`, write code that unwraps and prints it **only if it is even**. Try using optional binding with a condition.

```swift
var numberOfPeople: Int?

if Bool.random() {
    numberOfPeople = 108
}

if let numberOfPeople = numberOfPeople, numberOfPeople % 2 == 0 {
    print(numberOfPeople)
} else {
    print("Error: number of people may be nil or not even." )
}
```


## Question 15

Given the array of optional Ints `someNumbers`, write code to find the product of the array not including any nil values.

```swift
var someNumbers: [Int?] = []
var numbersToBeMultiplied: [Int] = []
var sum = 0

for i in 0..<20 {
    someNumbers.append(Bool.random() ? i : nil)
}

for number in someNumbers {
    if let number = number {
        numbersToBeMultiplied.append(number)
        sum += number
    }
}
    print(numbersToBeMultiplied,"Sum is:", sum)
```


## Question 16

Given the array `poorlyFormattedCityNames`, create a new array with the city names capitalized and any nil values removed.

```swift
let poorlyFormattedCityNames: [String?] = ["new york", "BOSTON", nil, "chicago", nil, "los angeles", nil, "Dallas",]

Output: ["New York", "Boston", "Chicago", "Los Angeles", "Dallas"]
```

```swift
let poorlyFormattedCityNames: [String?] = ["new york", "BOSTON", nil, "chicago", nil, "los angeles", nil, "Dallas",]
var outputArray = [String]()

for citiesToFormat in poorlyFormattedCityNames {
    if let city = citiesToFormat {
        outputArray.append(city.capitalized)
    }
}
print(outputArray)
```

## Question 17

Given a random array of optional numbers, create a new array of all the even numbers that aren't nil.

```swift
var aBunchOfNumbers: [Int?] = []
var outputArry = [Int]()

for _ in 0..<20 {
    aBunchOfNumbers.append(Bool.random() ? Int(arc4random_uniform(102)) : nil)
}

for optionalNum in aBunchOfNumbers {
    if let number = optionalNum {
        outputArry.append(number)
        }
}
print(outputArry)
```


## Question 18

Given the following array of zip codes as strings, write code that turns them into an array of Ints.

`let zipCodeStrings = ["11377", "11101", "11373", "10014", "10003", "11223"]`

```swift
let zipCodeStrings = ["11377", "11101", "11373", "10014", "10003", "11223"]
var zipCodeNum = [Int]()

for possibleZipCode in zipCodeStrings {
    if let zipcode = Int(possibleZipCode) {
        zipCodeNum.append(zipcode)
        }
}
print(zipCodeNum)
```


## Question 19
Some students were asked some questions about their favorite foods and colors and the answers were stored in an array `studentInfo`.

- Print the names of the students that do not have a favorite color.

- Print the names of the students that don't have a favorite color or a favorite food.

- Create a new array of type `[(String, String, String)]` that contains the students with both favorite colors and foods.

`let studentInfo: [(String, String?, String?)] = [("Bill", "Burgers", "Blue"), ("Rita", nil, "Red"), ("Peter", "Pizza", "Purple"), ("Sarah", "Sandwiches", nil), ("Jeff", nil, nil), ("Lucy", "Leftovers", "Lilac"), ("Mike", "Meat", "Mauve"), ("Gemma", nil, "Green")]`


```swift
let studentInfo: [(String, String?, String?)] = [("Bill", "Burgers", "Blue"), ("Rita", nil, "Red"), ("Peter", "Pizza", "Purple"), ("Sarah", "Sandwiches", nil), ("Jeff", nil, nil), ("Lucy", "Leftovers", "Lilac"), ("Mike", "Meat", "Mauve"), ("Gemma", nil, "Green")]

var noFavoriteColorNames = [String]()
var noFavoriteFoodNames = [String]()
var noFavoriteColorNorFood = [String]()
var bothFavoriteColorAndFood = [(String, String, String)]()

for studentTuple in studentInfo {
    if studentTuple.1 == nil && studentTuple.2 == nil {
        noFavoriteColorNorFood.append(studentTuple.0)
    }
    if studentTuple.1 == nil {
        FavoriteFoodNames.append(studentTuple.0)
    }
    if studentTuple.2 == nil {
        noFavoriteColorNames.append(studentTuple.0)
    }
    if studentTuple.1 != nil && studentTuple.2 != nil {
        let validStudent = (studentTuple.0, studentTuple.1!, studentTuple.2!)
        bothFavoriteColorAndFood.append(validStudent)
    }
}

// Print the names of the students that do not have a favorite color.
print("Names of students that do not have a favorite color:", noFavoriteColorNames, separator: "\n")

// Print the names of the students that don't have a favorite color or a favorite food.
print("Names of students that do not have a favorite color or food:", noFavoriteColorNorFood, separator: "\n")

// Names of students with all information filled out
print("Names of students with information all filled out:", bothFavoriteColorAndFood, separator: "\n")
```


## Question 20

Given an optional array of optional tuples of optional UInt8s,

- Write code to safely unwrap and print the tuples in the array with all 3 RGB values.

- Write code that counts all the nil values.

`let possibleColors: [(r: UInt8?, g: UInt8?, b: UInt8?)?]? = [(128, 21, 7), (0, 0, 0), nil, (nil, 25, 82), (255, 255, 255), nil, (200, 100, nil), (120, nil, 23), (0, 255, 106), (nil, nil, nil), nil, (100, 100, 200)]`


```swift
let possibleColors: [(r: UInt8?, g: UInt8?, b: UInt8?)?]? = [(128, 21, 7), (0, 0, 0), nil, (nil, 25, 82), (255, 255, 255), nil, (200, 100, nil), (120, nil, 23), (0, 255, 106), (nil, nil, nil), nil, (100, 100, 200)]
var nilRgbTupleCount = 0
var nilrgbColorCount = 0
var validColors = [(UInt8, UInt8, UInt8)]()

if let posibleColorsArray = possibleColors {
    for possibleRGB in posibleColorsArray {
        let fullRGB: (UInt8, UInt8, UInt8)
        if let RGB = possibleRGB {
            if RGB.0 == nil{
                nilrgbColorCount += 1
            }
            if RGB.1 == nil{
                nilrgbColorCount += 1
            }
            if RGB.2 == nil{
                nilrgbColorCount += 1
            }
            if RGB.0 != nil && RGB.1 != nil && RGB.2 != nil{
                fullRGB = (RGB.0!,RGB.1!,RGB.2!)
                validColors.append(fullRGB)
            }
        } else {
            nilRgbTupleCount += 1
        }
    }
} else {
    print("Error: No colors in your array.")
}

// Write code to safely unwrap and print the tuples in the array with all 3 RGB values.
print("Tuples with three RGB values:", validColors, separator: "\n")

// Write code that counts all the nil values.
print("Number of nil RGB Tuples:", nilRgbTupleCount, separator: "\n")
print("Number of nil RGB values:", nilrgbColorCount, separator: "\n")
```
## Question 21

Consider the following nested optional. It corresponds to a number inside a box inside a box inside a box.

- Fully force unwrap and print number.

- Optionally bind and print number.

`let number: Int??? = 10`

```swift
let number: Int??? = 10

// Fully force unwrap and print number.
print(number!!!)

// Optionally bind and print number.
if let number1 = number, let number2 = number1, let number3 = number2 {
    print(number3)
}
```


## Question 22

Given an Array of Optional Strings, write code that concatenates all non-nil values together except for strings with 3 or more vowels.

`let monkeyingAround = ["orangutan", "apes",nil, "monkeys", "gorillas", "lemurs", nil]`

output: `"apesmonkeyslemurs"`

```swift
let monkeyingAround = ["orangutan", "apes",nil, "monkeys", "gorillas", "lemurs", nil]

let vowels = ["a","e","i","o","u"]
var vowelCounter = 0
var outputString = ""


for potentialString in monkeyingAround {
    if let string = potentialString {
        for character in string where vowels.contains(String(character)){
            vowelCounter += 1
        }
        if vowelCounter < 3 {
            outputString.append(string)
        }
        vowelCounter = 0
    }
}
print(outputString)
```


## Question 23 Need to finish

Given the value below, print out all of the non-nil Ints it contains by accessing each of them.

`var strangeStructure: ([Int]?, [[Int?]], [[Int]?], Int)? = ([1], [[2,3,4],[],[5,nil],[nil]], [nil, [6,7,8],nil,[],[9]], 10)`

```swift
var strangeStructure: ([Int]?, [[Int?]], [[Int]?], Int)? = ([1], [[2,3,4],[],[5,nil],[nil]], [nil, [6,7,8],nil,[],[9]], 10)

var numbersToPrint = [Int]()

    if let possibleStructure = strangeStructure {
        // optional array in position 0
        if let positionOne = possibleStructure.0 {
            for integer in positionOne {
                numbersToPrint.append(integer)
            }
        }
        // array of array of optional Ints in position 1
        for array in possibleStructure.1 {
            for optionalInt in array {
                if let integer = optionalInt {
                    numbersToPrint.append(integer)
                }
            }
        }
        // array of optional array of Ints in position 2
        for optionalArray in possibleStructure.2 {
            if let array = optionalArray {
                for integer in array {
                    numbersToPrint.append(integer)
                }
            }
        }
        // Int in position 3
        numbersToPrint.append(possibleStructure.3)
    }
// print numbers to print
for integer in numbersToPrint {
    print(integer, terminator: " ")
}
````
