# Swift-for-Caveman

#### Variables
<b>let</b> is for constants and you can't change it

<b>var</b> is for dynamic


    let NAME = "Daniel"
    var newName = "David"

    newName = "Alex"

    // single line declaration
    var x = 0.0, y = 0.0, z = 0.0


    // type of annotations
    var welcomeMessage: String
    welcomeMessage = "Hello"


    // same type in single line declaration
    var red, green, yello, blue: Double


    println(welcomeMessage + " " + newName)
    println(welcomeMessage + " \(newName)")


##### Numbers

    let minValueUint8 = UInt8.min
    let maxValueUint8 = UInt8.max
    // let maxValueUint8 = UINT8_MAX
    let minValueInt8 = INT8_MIN


    // UInt without number indicate the unsigned integer of the 
    // running device
    let myDeviceInt:UInt = UInt.max


    // Numeric Literals
    let paddedDouble = 000123.456
    let oneMillion = 1_000_000


    // converting numbers
    let doubleToInteger = Int(paddedDouble)


#### Semicolons
Let you to write more statement in single line

    let cat = "😸"; let helloKitty = "Hi"; println(helloKitty + " \(cat)");


#### Type Aliases
let you define alternate name for existing type. Remember typealiases is for system type.

    typealias AudioSample = UInt16
    let maxAudioSampleFound: AudioSample = 0


    typealias myImage = UIImage
    let avatar:myImage


#### Bool

    var awesomeBool: Bool = false

##### Tuples
Tuples group multiple values into a single compund value.

    let helloTuple = (123, "what's up", "awesome",["yes"],404)
    let http404Error = (404, "not Found")

    println(http404Error.0)

    let (statusCode, statusMessage) = http404Error

    // if you only need some of the tuple value with ignoring others
    let (_,justGiveMeStatus,_,_,_) = helloTuple


    // You can name the individual element in tuple
    let http202Error = (statusCode: 200, description: "Ok")

    println(http202Error.0)
    println(http202Error.statusCode)


#### Optional 

    let convertetNumber = "123".toInt()
    var serverResponseCode: Int? = 404
    serverResponseCode = nil


#### Optional Binding
you can use optional binding to find out whether an optional contains a value, and if so, to make that value available

    if let awesomeNumber = "1234".toInt(){
        // converted value
        println(awesomeNumber)
    }else{
        // failed to convert
    }


    // multiple optional binding
    if let awesomeNum1 = "123".toInt(), awesomeNum2 = "43".toInt(){
        // converted value
        println(awesomeNum1+awesomeNum2)
    }else{
        // failed to convert
    }

#### Implicitly Unwrapped Optional 
* As described above, optional allowed to have nil value.
* But sometimes its clear for programmer that its really 
* have a value.
* so you write an implicitly unwrapped optional using `!`

    let possibleString: String? = "An Optional String"
    let forcedString: String = possibleString!


#### Assertions 
* assertion is a runtime check that a logical condition is true
* when xcode running your app in debug mode and checks for assert

    let age = -3
    // assert(age >= 0 , "A person's age cannot be less than zero")
    // this cause assertion to be trigerred


##### Operations 
    var a = 11
    var b = 7

    var c: Int = a & b   // AND
    c = a | b           // OR
    c = a ^ b           // XOR

    c = a++

    println(a)
    println(c)


    // nil coalescing operator
    // a ?? b
    // unwrap an optional a if it contains a value, or return a default value b


    var awesomeNumbers = a ?? 3
    var randomName: String?
    let colorName = randomName ?? "Blue"

    randomName = "green"
    let colorName2 = randomName ?? "Blue"


    // Range Operator
    for index in 1...3 {
        println("hi \(index)")
    }

#### Arrays
    let names = ["Anna","alex","Jack","David"]
    for i in 0..<names.count {
        println("hi \(names[i])")
    }

    for i in "hello" {
        println(i)
    }

    for i in indices("hello") {
        println(i)
    }


    let exclamationMark: Character = "!"


    var someInts = [Int]()
    var someAnotherInts: [Int] = Array()
    var anotherInts: [Int] = []

    var threeDoubles = [Double](count: 3, repeatedValue: 3.0)
    threeDoubles[0...1] = [2.0,2.0]
    println(threeDoubles)


    for (index,value) in enumerate(names) {
        println("\n index \(index) and value of \(value)")
    }

    for _ in 1...names.count {
        println("no i")
    }

##### Sets
* set stores distinct values of the same type in a collection with no
* defined ordering. You can use set alternate to array when the order
* of the items is not important, or when you need to ensure that an item
* ONLY appear once.

    var letters = Set<Character>()
    letters = ["c","b","b","b","b","b"]
    letters.count

    if letters.contains("c"){
        letters.insert("a")
    }


    // sorted does not have ordering
    // thus you can use global sorted function

    for char in sorted(letters){
        println(char)
    }


#### Dictionary 
    var nameOfIntegers = [Int: String]()
    nameOfIntegers[16] = "Sixteen"
    nameOfIntegers = [:] // make dictionary empty

#### Switch
    let someChar: Character = "e"
    switch someChar {
        case "a","b","d":
            println("this one a b d")
        case "c","f","e":
            println("this one c f e")
        default:
            println("the rest")
    }

    let somePoint = (1,1)
    switch somePoint{
        case (0,0):
            println("this is 0 0")
        case(_,0):
            println("the y is 0")
        case(0,_):
            println("the x is 0")
        case(-2...2,-2...2):
            println("its between -2 ... 2")
        default:
            println("ok")
    }

    switch somePoint{
    case (let x,0):
        println("this is \(x)")
    case let(x,y):
        println("the y is \(y) and x \(x)")
    default:
        println("ok")
    }

    // using where statement
    var desc = ""
    switch somePoint{
        case let(x,y) where x == y:
            desc += "the x < y "
            fallthrough
        default:
            desc += "ok, this also reads default"
    }

    println(desc)

    // Control transfer Statements
    // - continue: tell the loop stop & start again from begining
    // - break: end executation of an entire control flow
    // - fallthrough: only for switch statements
    // - return


##### Functions

    func sayHello(personName: String) -> String {
        return "hello \(personName)"
    }

    println(sayHello("David"))

    // in order to show parameter name you can use another name before the local name
    func sayGoodbye(userName name: String) {
        println("hi")
    }

    sayGoodbye(userName: "David")

    // short version we could use '#'
    func sayGoodbyeAgain(#name: String){
        //
    }

    sayGoodbyeAgain(name: "david")


    // default parameter
    func awesomeDefault(name :String = "Daniel"){
            // this has default name
    }

    // function param are constant by default
    // if you want to change them add 'var' before it
    func varParams(var name: String){
        name = "I changed"
    }

    // in-out function
    func swapMyValues(inout a: Int,inout b:Int){
        let tempA = a
        a = b
        b = tempA
    }

    var someInt1 = 13, someInt2 = 20

    swapMyValues(&someInt1, &someInt2)
    println("value 1:\(someInt1) and 2:\(someInt2) has changed")

