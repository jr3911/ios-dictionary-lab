# Dictionaries lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1

- Create an instance of a dictionary called `citiesDict` that maps 3 countries to their capital cities.

- Add two more countries to your dictionary.

- Translate at least 3 of the capital names into another language.

```swift
var citiesDict: [String:String] = ["United Arab Emirates":"Abu Dhabi", "Netherlands":"Amsterdam", "Thailand":"Bangkok"]

citiesDict["China"] = "Beijing"
citiesDict["Germany"] = "Berlin"

citiesDict["Germany"] = "ベルリン"      //Berlin in Japanese
citiesDict["United Arab Emirates"] = "アブダビ"     //Abu Dhabi in Japanese
citiesDict["Netherlands"] = "アムステルダム"       //Amsterdam in Japanese

print(citiesDict)
```


## Question 2

`var someDict:[String:Int] = ["One": 1, "Two": 4, "Three": 9, "Four": 16, "Five": 25]`

- Using `someDict`, add together the values associated with "Three" and "Five" and print the result.

- Add values to the dictionary for the keys "Six" and "Seven".

- Make a key called `productUpToSeven` and set its value equal to the product of all the values.

- Make a key called `sumUpToSix` and set its value equal to the sum of the keys "One", "Two", "Three", "Four", "Five" and "Six".

- Remove the new keys made in the previous two steps

- Add 2 to every value inside of `someDict`.

```swift
var someDict:[String:Int] = ["One": 1, "Two": 4, "Three": 9, "Four": 16, "Five": 25]

//prints the result of "Three" and "Five"
print("Sum of 'Three' and 'Five': \(someDict["Three"]! + someDict["Five"]!)")

//Adds keys and values for "Six" and "Seven"
someDict["Six"] = 36
someDict["Seven"] = 49
print("Keys for 'Six' and 'Seven' have been created")

//makes a key "productUpToSeven" and sets its value to be the product of all values
someDict["productUpToSeven"] = 1
for v in someDict.values {
    someDict["productUpToSeven"] = someDict["productUpToSeven"]! * v
}
print("Product of all the values up to 'Seven': \(someDict["productUpToSeven"]!)")

someDict["sumUpToSix"] = 0
for v in someDict.values {
    if v != someDict["productUpToSeven"]! {
        someDict["sumUpToSix"]! += v
    }
}
print("Sum of values 'One' through 'Six': \(someDict["sumUpToSix"]!)")

//removes the new keys made in the previous two steps 'productUpToSeven' and 'sumUpToSix'
someDict.removeValue(forKey: "productUpToSeven")
someDict.removeValue(forKey: "sumUpToSix")
print("Keys for 'productUpToSeven' and 'sumUpToSix' have been removed")

//adds 2 to every value inside 'someDict'
for (key, value) in someDict {
    someDict[key] = value + 2
}
print(someDict)

```


## Question 3

Create a variable that is explicitly typed as a dictionary that maps strings to floating point numbers. Initialize the variable to the data shown in the table below which lists an author name and their comprehensibility score.

| Author Name |	Score |
| :--: | :--: |
| Mark Twain |	8.9 |
| Nathaniel Hawthorne	| 5.1 |
| John Steinbeck	| 2.3 |
| C.S. Lewis | 9.9 |
| Jon Krakauer | 6.1 |

Using the dictionary created in the previous problem, do the following:

- Print out the floating-point score for “John Steinbeck”.

- Add an additional author named “Erik Larson” with an assigned score of 9.2.

- Write an if/else statement that compares the score of John Krakaur with Mark Twain. Print out the name of the author with the highest score.

- Use a for-loop to iterate through the dictionary you created at the beginning of the problem, and print out the content in the form of key: value, one entry per line.

```swift
var authorAndScore: [String:Float] = ["Mark Twain":8.9, "Nathaniel Hawthorne":5.1, "John Steinbeck":2.3, "C.S. Lewis":9.9, "Jon Krakauer":6.1]

//prints the floating-point score for John Steinbeck
print("John Steinbeck's comprehensibility score: \(authorAndScore["John Steinbeck"]!)")

//add key 'Erk Larson' with value '9.2'
authorAndScore["Erik Larson"] = 9.2
print("Erik Larson has been added with a comprehensibility score of 9.2")

//prints which author has the higher score between the two
if authorAndScore["Jon Krakauer"]! != authorAndScore["Mark Twain"]! {
    if authorAndScore["Jon Krakauer"]! > authorAndScore["Mark Twain"]! {
        print("Jon Krakauer has a higher score than Mark Twain")
    } else {
        print("Mark Twain has a higher score than Jon Krakauer")
    }
} else {
    print("Jon Krakauer and Mark Twain have the same comprehensibility scores")
}

// iterates through the dictionary and prints out each entry
for (key, value) in authorAndScore {
    print("\(key): \(value)")
}
```


## Question 4

You are given a dictionary code of type [String:String] which has values for all lowercase letters. The code dictionary represents a way to encode a message. For example if code["a"] = "z" and code["b"] = "x" the encoded version if "ababa" will be "zxzxz". You are also given a message which contains only lowercase letters and spaces. Use the `code` dictionary below to encode the message and print it.

```swift
var code = [
    "a" : "b",
    "b" : "c",
    "c" : "d",
    "d" : "e",
    "e" : "f",
    "f" : "g",
    "g" : "h",
    "h" : "i",
    "i" : "j",
    "j" : "k",
    "k" : "l",
    "l" : "m",
    "m" : "n",
    "n" : "o",
    "o" : "p",
    "p" : "q",
    "q" : "r",
    "r" : "s",
    "s" : "t",
    "t" : "u",
    "u" : "v",
    "v" : "w",
    "w" : "x",
    "x" : "y",
    "y" : "z",
    "z" : "a"
]

var message = "hello world"
var encodedMessage = ""

for char in message {
    code[String(char)] = code[String(char)] ?? " "
    encodedMessage += code[String(char)]!
}
print(encodedMessage)

//Part Two of Question - Decoding an encoded message
encodedMessage = "uijt nfttbhf jt ibse up sfbe"
var decodedMessage = ""

//decoding and printing the decodedMessage
for char in encodedMessage {
    //checks if the character in the encoded message is a space (not included in the code) and just add it to the decodedMessage
    if char == " " {
        decodedMessage += " "
    } else {
        //if the char is not a white space, then cross reference it to the values in code and give back the corresponding key, then add to decodedMessage
        for entry in code {
            if let letter = code[entry.key] {
                if String(char) == letter {
                decodedMessage += entry.key
                }
            }
        }
    }
}
print(decodedMessage)

```

You are also given an `encodedMessage` which contains only lowercase letters and spaces. Use the `code` dictionary to decode the message and print it.
`var encodedMessage = "uijt nfttbhf jt ibse up sfbe"`


## Question 5

You are given an array of dictionaries. Each dictionary in the array contains exactly 2 keys `“firstName”` and `“lastName”`. Create an array of strings called `firstNames` that contains only the values for `“firstName”` from each dictionary.

```swift
var people: [[String:String]] = [
    [
        "firstName": "Calvin",
        "lastName": "Newton"
    ],
    [
        "firstName": "Garry",
        "lastName": "Mckenzie"
    ],
    [
        "firstName": "Leah",
        "lastName": "Rivera"
    ],
    [
        "firstName": "Sonja",
        "lastName": "Moreno"
    ],
    [
        "firstName": "Noel",
        "lastName": "Bowen"
    ]
]

//firstNames
var firstNames = [String] ()
for dictionary in people {
    for key in dictionary.keys {
        if key == "firstName" {
            firstNames.append(dictionary[key]!)
        }
    }
}
print(firstNames)

//fullNames
var fullNames = [String] ()
for dictionary in people {
    fullNames.append(dictionary["firstName"]! + " " + dictionary["lastName"]!)
}
print(fullNames)
```

Now, create an array of strings called `fullNames` that contains the values for `“firstName”` and `“lastName”` from the dictionary separated by a space.


## Question 6

You are given an array of dictionaries. Each dictionary in the array describes the score of a person. Find the person with the best score and print his full name.

```swift
var peopleWithScores: [[String: String]] = [
    [
        "firstName": "Calvin",
        "lastName": "Newton",
        "score": "13"
    ],
    [
        "firstName": "Garry",
        "lastName": "Mckenzie",
        "score": "23"
    ],
    [
        "firstName": "Leah",
        "lastName": "Rivera",
        "score": "10"
    ],
    [
        "firstName": "Sonja",
        "lastName": "Moreno",
        "score": "3"
    ],
    [
        "firstName": "Noel",
        "lastName": "Bowen",
        "score": "16"
    ]
]

var highestScore: Int = 0
var highestPlayer: String = ""

for dictionary in peopleWithScores {
    for key in dictionary.keys {
        if key == "score" {
            if let stringScore = dictionary["score"] {
                let numberScore = Int(stringScore)!
                if numberScore > highestScore {
                    highestScore = numberScore
                    highestPlayer = ("\(dictionary["firstName"] ?? "Unavailable") \(dictionary["lastName"] ?? "Unavailable")")
                }
            }
        }
    }
}
print("\(highestPlayer): \(highestScore)")

```

Print out the dictionary above in the following format:  **full name - score**


## Question 7

`var numbers = [1, 2, 3, 2, 3, 5, 2, 1, 3, 4, 2, 2, 2]`

You are given an array of integers. The frequency of a number is the number of times it appears in the array. Find out the frequency of each one.

Print the numbers in ascending order followed by their frequency.

```swift
var numbers = [1, 2, 3, 2, 3, 5, 2, 1, 3, 4, 2, 2, 2]
var numTracker = 0

//creating an array of unique integers to use as keys for dictionary
var dictKeys = [Int]()
for num in numbers {
    if dictKeys.contains(num) == false {
        dictKeys.append(num)
    }
}

//creating dictionary using the above array and iterating through both it and the original array
//keep tracker of the specific number that corresponds to the key
var dictionary: [Int:Int] = [:]
for k in dictKeys {
    numTracker = 0
    for num in numbers{
        if num == k {
            numTracker += 1
            dictionary[k] = numTracker
        }
    }
}
print(dictionary)
```

## Question 8

Print the most common letter in the string below:

`var myString = "We're flooding people with information. We need to feed it through a processor. A human must turn information into intelligence or knowledge. We've tended to forget that no computer will ever ask a new question."`

```swift
var myString = "We're flooding people with information. We need to feed it through a processor. A human must turn information into intelligence or knowledge. We've tended to forget that no computer will ever ask a new question."

//creating array to use as reference when making keys for dicitonary
var alphabet = "qwertyuiopasdfghjklzxcvbnm"
var dictAlphabet = [Character]()
    for char in myString {
        if alphabet.contains(char) {
            if dictAlphabet.contains(char) == false {
                dictAlphabet.append(char)
        }
    }
}

// creating a dictionary with keys from above and updating each key's value with a counting variable
var dictionary: [Character:Int] = [:]
var charTracker = 0
for k in dictAlphabet {
    for char in myString {
        if char == k {
            charTracker += 1
            dictionary[k] = charTracker
        }
    }
}

//iterating through the dictionary and keeping track/updating which letter has the most occurrences
var mostOccurrences = 0
var letterWithMostOccurrences: Character = " "
for key in dictionary.keys {
    if dictionary[key]! > mostOccurrences {
        mostOccurrences = dictionary[key]!
        letterWithMostOccurrences = key
    }
}
print("'\(letterWithMostOccurrences)', with \(dictionary[letterWithMostOccurrences]!) number of frequencies")

```

## Question 9

Write code that creates a dictionary where the keys are Ints between 0 and 20 inclusive, and each key's value is its cube.

```swift
var zeroTwentyDict: [Int:Int] = [:]

for i in 0...20 {
    zeroTwentyDict[i] = i * i
}
print(zeroTwentyDict)
```


## Question 10

Write code that iterates through `testStates` and prints out whether or not that key is in `statePop`.

```swift
let statePop = ["Alabama": 4.8, "Alaska": 0.7, "Arizona": 6.7, "Arkansas": 3.0]
let testStates = ["California","Arizona", "Alabama", "New Mexico"]

var verification = false

for state in testStates {
    verification = false
    for key in statePop.keys {
        if state == key {
            verification = true
            break
        }
    }
    if verification == true {
        print("\(state) is a key in statePop")
    } else {
        print("\(state) is not in statePop")
    }
}

```


## Question 11

You are given the dictionary `deposits`, which maps a persons name to an array of deposits that have been made to their account.

a) Write code to to print the name and total amount deposited of the person who recieved the most money.

b) Create an array called `stolenCents`, iterate over deposits for each person and steal their cents! ... like Office Space or Superman 3. Calculate the decimal part of each value, add it to the `stolenCents` array and round down the value in the dict.

c) How much money did you steal?

```swift
var deposits: [String: [Double]] = [
 "Williams" : [300.65, 270.45, 24.70, 52.00, 99.99],
 "Cooper" : [200.56, 55.00, 600.78, 305.15, 410.76, 35.00],
 "Davies" : [400.98, 56.98, 300.00],
 "Clark" : [555.23, 45.67, 99.95, 80.76, 56.99, 46.50, 265.70],
 "Johnson" : [12.56, 300.00, 640.50, 255.60, 26.88]
]

var highestDeposit = 0.0
var highBaller = ""

for (name, money) in deposits {
    if money.reduce(0,+) > highestDeposit {
        highestDeposit = money.reduce(0,+)
        highBaller = name
    }
}

var adjustedMoney = String(format: "%.2f", highestDeposit)
print("\(highBaller) has the most money: $\(adjustedMoney)")
```


## Question 12

Print the second most common letter in the string below:

`var myString = "We're flooding people with information. We need to feed it through a processor. A human must turn information into intelligence or knowledge. We've tended to forget that no computer will ever ask a new question."`

```swift
var myString = "We're flooding people with information. We need to feed it through a processor. A human must turn information into intelligence or knowledge. We've tended to forget that no computer will ever ask a new question."


//creating array to use as reference when making keys for dicitonary
var alphabet = "qwertyuiopasdfghjklzxcvbnm"
var dictAlphabet = [Character]()
for char in myString {
    if alphabet.contains(char) {
        if dictAlphabet.contains(char) == false {
            dictAlphabet.append(char)
        }
    }
}

// creating a dictionary with keys from above and updating each key's value with a counting variable
var dictionary: [Character:Int] = [:]
var charTracker = 0
for k in dictAlphabet {
    for char in myString {
        if char == k {
            charTracker += 1
            dictionary[k] = charTracker
        }
    }
}

//iterating through the dictionary and keeping track/updating which letter has the most occurrences
var mostOccurrences = 0
var letterWithMostOccurrences: Character = " "
var secondMostOccurrences = 0
var secondMostLetter: Character = " "

for key in dictionary.keys {
    if dictionary[key]! > mostOccurrences {
        //update the second most common before updating the most common
        secondMostLetter = letterWithMostOccurrences
        secondMostOccurrences = mostOccurrences
        //update the most common
        mostOccurrences = dictionary[key]!
        letterWithMostOccurrences = key
    }
}
print("'\(secondMostLetter)', with \(secondMostOccurrences) number of frequencies")
```


## Question 13

Given the below 4 arrays of Ints,

a) create a new array, sorted in ascending order, that contains all the values without duplicates.

b) create another new array that contains unique values that appear in all 4 arrays.

```swift
let arr1 = [2, 4, 5, 6, 8, 10, 12]
let arr2 = [1, 2, 3, 4, 5, 6]
let arr3 = [5, 6, 7, 8, 9, 10, 11, 12]
let arr4 = [1, 3, 4, 5, 6, 7, 9]

// creating new array and appending values through loops if array does not already contain the value at that point thus far.
var arr5 = [Int]()

for num in arr1 + arr2 + arr3 + arr4 where arr5.contains(num) == false {
    arr5.append(num)
}
//sorting the array in ascending order
arr5 = arr5.sorted()

print(arr5)

//creating new array that contains only unique values that appear in all 4 arrays
var arr6 = [Int]()
for num in arr1 + arr2 + arr3 + arr4 where arr6.contains(num) == false && arr1.contains(num) == true && arr2.contains(num) == true && arr3.contains(num) == true && arr4.contains(num) == true {
    arr6.append(num)
}

arr6 = arr6.sorted()

print(arr6)

```


## Question 14

Given the following exert from the Declaration of Independence, find the most frequent word that is longer than 5 characters.

 - use `components(separatedBy:)` to break up the string into an array.

 - use `CharacterSet.punctuationCharacters` in union with any other characters you don't want in your array, like spaces and new lines.

 ```swift
let declarationOfIndependence = """
When in the Course of human events, it becomes necessary for one people to dissolve the
political bands which have connected them with another, and to assume among the powers of the
earth, the separate and equal station to which the Laws of Nature and of Nature's God entitle
them, a decent respect to the opinions of mankind requires that they should declare the causes
which impel them to the separation.

We hold these truths to be self-evident, that all men are created equal, that they are endowed by
their Creator with certain unalienable Rights, that among these are Life, Liberty and the pursuit
of Happiness. That to secure these rights, Governments are instituted among Men, deriving
their just powers from the consent of the governed, That whenever any Form of Government
becomes destructive of these ends, it is the Right of the People to alter or to abolish it, and to
institute new Government, laying its foundation on such principles and organizing its powers in
such form, as to them shall seem most likely to effect their Safety and Happiness. Prudence,
indeed, will dictate that Governments long established should not be changed for light and
transient causes; and accordingly all experience hath shewn, that mankind are more disposed to
suffer, while evils are sufferable, than to right themselves by abolishing the forms to which they
are accustomed. But when a long train of abuses and usurpations, pursuing invariably the same
Object evinces a design to reduce them under absolute Despotism, it is their right, it is their duty,
to throw off such Government, and to provide new Guards for their future security. Such has
been the patient sufferance of these Colonies; and such is now the necessity which constrains
them to alter their former Systems of Government. The history of the present King of Great
Britain is a history of repeated injuries and usurpations, all having in direct object the
establishment of an absolute Tyranny over these States. To prove this, let Facts be submitted to a
candid world.
"""
```
