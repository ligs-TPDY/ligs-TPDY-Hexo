---
title: The Swift Programming Language (4.0)(翻译)
date: 2018-09-11 16:39:26
tags: Swift
---
#####    一直以来，我都想好好的研究研究一下这个新语言。之前虽然用过一段时间，但一直都觉得不甚了解。这本书已经得到了好久，期间也断断续续的读过，但我的英文水平有限，所以也就是看看示例代码而已。这次，又捡起这本书。想着可怜巴巴的英文水平，就想着借这个机会翻译翻译，即便是多数情况要借助翻译工具，但接触的多了，我的英文水平总该有所改善吧。同时又可以细化自己对这门语言的理解。记得有位大神说过：想让自己的水平提高，就试着写自己的博客吧。
#####    自己最早接触的语言是C，后来做iOS开发，学习了OC语言。对python，js和java有点模糊的认知。记得刚接触OC时，就无数次的接触这样一个名词：“面向对象”。在将近3年的开发经历中，一直都是使用OC。自从1年前开始接触swift，发现这个新语言真真的是好用。奈何现在公司的项目还没有考虑使用这门语言，所以，自己只能随便搞搞。最近的工作紧张起来，希望自己可以坚持翻译。
# Welcome to Swift
## About Swift
##### “Swift is a fantastic way to write software, whether it’s for phones, desktops, servers, or anything else that runs code. It’s a safe, fast, and interactive programming language that combines the best in modern language thinking with wisdom from the wider Apple engineering culture and the diverse contributions from its open-source community. The compiler is optimized for performance and the language is optimized for development, without compromising on either.”

###### “Swift是编写软件的绝佳方式，无论是用于手机，台式机，服务器还是其他任何运行代码的软件。 它是一种安全，快速，交互式的编程语言，它将现代语言思维的最佳结合与来自更广泛的Apple工程文化的智慧和来自开源社区的各种贡献相结合。 编译器针对性能进行了优化，语言针对开发进行了优化，而且不会影响任何一个。”

##### “Swift is friendly to new programmers. It’s an industrial-quality programming language that’s as expressive and enjoyable as a scripting language. Writing Swift code in a playground lets you experiment with code and see the results immediately, without the overhead of building and running an app.”
###### “Swift对新程序员友好。 它是一种工业级编程语言，与脚本语言一样富有表现力和乐趣。 在游乐场中编写Swift代码可以让您试验代码并立即查看结果，而无需构建和运行应用程序的开销。”
##### “Swift defines away large classes of common programming errors by adopting modern programming patterns:”“Variables are always initialized before use.Array indices are checked for out-of-bounds errors.Integers are checked for overflow.Optionals ensure that nil values are handled explicitly.Memory is managed automatically.Error handling allows controlled recovery from unexpected failures.”
###### “Swift通过采用现代编程模式来定义大类常见的编程错误：”
    “变量总是在使用前初始化。
    检查数组索引是否存在越界错误。
    检查整数是否溢出。
    Optionals确保明确处理nil值。
    内存自动管理。
    错误处理允许从意外故障中进行受控恢复。”
##### “Swift code is compiled and optimized to get the most out of modern hardware. The syntax and standard library have been designed based on the guiding principle that the obvious way to write your code should also perform the best. Its combination of safety and speed make Swift an excellent choice for everything from “Hello, world!” to an entire operating system.”
###### “Swift代码经过编译和优化，可以充分利用现代硬件。 语法和标准库的设计基于指导原则，即编写代码的明显方法也应该表现最佳。 它的安全性和速度相结合，使Swift成为从“Hello，world！”到整个操作系统的绝佳选择。”
##### “Swift combines powerful type inference and pattern matching with a modern, lightweight syntax, allowing complex ideas to be expressed in a clear and concise manner. As a result, code is not just easier to write, but easier to read and maintain as well.”
###### 该语言使用强大的类型推断和现代的模式匹配功能，轻便的语法，“允许以清晰简洁的方式表达复杂的想法”，总而言之，代码不仅简单易读，而且容易维护。
##### “Swift has been years in the making, and it continues to evolve with new features and capabilities. Our goals for Swift are ambitious. We can’t wait to see what you create with it.”
###### “Swift多年来一直在不断发展，并且随着新特性和功能的不断发展而不断发展。 我们对Swift的目标雄心勃勃。 我们迫不及待地想看看你用它创造了什么。“   
## Version Compatibility
##### “This book describes Swift 4.0, the default version of Swift that’s included in Xcode 9. You can use Xcode 9 to build targets that are written in either Swift 4 or Swift 3.”
###### “本书描述了Swift 4.0，它是Xcode 9中包含的Swift的默认版本。您可以使用Xcode 9构建以Swift 4或Swift 3编写的目标。”
    
##### “When you use Xcode 9 to build Swift 3 code, most of the new Swift 4 functionality is available. That said, the following features are available only to Swift 4 code:
##### Substring operations return an instance of the Substring type, instead of String.
##### The @objc attribute is implicitly added in fewer places.
##### Extensions to a type in the same file can access that type’s private members.
###### “当您使用Xcode 9构建Swift 3代码时，大多数新的Swift 4功能都可用。 也就是说，以下功能仅适用于Swift 4代码：
###### 子串操作返回Substring类型的实例，而不是String。
###### @objc属性隐式添加在更少的位置。
###### 对同一文件中的类型的扩展可以访问该类型的私有成员。
    
##### “A target written in Swift 4 can depend on a target that’s written in Swift 3, and vice versa. This means, if you have a large project that’s divided into multiple frameworks, you can migrate your code from Swift 3 to Swift 4 one framework at a time.”
###### “用Swift 4编写的目标可以依赖于用Swift 3编写的目标，反之亦然。 这意味着，如果您有一个分为多个框架的大型项目，您可以一次将代码从Swift 3迁移到Swift 4一个框架。”

## A Swift Tour
###### “Tradition suggests that the first program in a new language should print the words “Hello, world!” on the screen. In Swift, this can be done in a single line:”
    print("Hello, world!")
###### “If you have written code in C or Objective-C, this syntax looks familiar to you—in Swift, this line of code is a complete program. You don’t need to import a separate library for functionality like input/output or string handling. Code written at global scope is used as the entry point for the program, so you don’t need a main() function. You also don’t need to write semicolons at the end of every statement.”
###### “如果你用C或Objective-C编写代码，这个语法看起来很熟悉 - 在Swift中，这行代码是一个完整的程序。 您无需为输入/输出或字符串处理等功能导入单独的库。 在全局范围编写的代码用作程序的入口点，因此您不需要main（）函数。 你也不需要在每个语句的末尾写分号。”
    
###### “This tour gives you enough information to start writing code in Swift by showing you how to accomplish a variety of programming tasks. Don’t worry if you don’t understand something—everything introduced in this tour is explained in detail in the rest of this book.”
###### “通过向您展示如何完成各种编程任务，本导览为您提供了足够的信息来开始在Swift中编写代码。 如果您不理解某些内容，请不要担心 - 本书其余部分将详细介绍本次导览中介绍的所有内容。”
    
## Simple Values
###### “Use let to make a constant and var to make a variable. The value of a constant doesn’t need to be known at compile time, but you must assign it a value exactly once. This means you can use constants to name a value that you determine once but use in many places.”
    “var myVariable = 42
    myVariable = 50
    let myConstant = 42”
###### “使用let来创建常量，使用var来创建变量。 在编译时不需要知道常量的值，但必须为其分配一次值。 这意味着您可以使用常量来命名您确定一次但在许多地方使用的值。”
######　“A constant or variable must have the same type as the value you want to assign to it. However, you don’t always have to write the type explicitly. Providing a value when you create a constant or variable lets the compiler infer its type. In the example above, the compiler infers that myVariable is an integer because its initial value is an integer.”
###### “常量或变量必须与要分配给它的值具有相同的类型。 但是，您并不总是必须明确地写入类型。 在创建常量或变量时提供值可让编译器推断其类型。 在上面的例子中，编译器推断myVariable是一个整数，因为它的初始值是一个整数。”
##### “If the initial value doesn’t provide enough information (or if there is no initial value), specify the type by writing it after the variable, separated by a colon.”
###### “如果初始值没有提供足够的信息（或者没有初始值），则通过在变量之后写入来指定类型，用冒号分隔。”
    “let implicitInteger = 70
    let implicitDouble = 70.0
    let explicitDouble: Double = 70”
###### “Values are never implicitly converted to another type. If you need to convert a value to a different type, explicitly make an instance of the desired type.”
    “let label = "The width is "
    let width = 94
    let widthLabel = label + String(width)”
###### “There’s an even simpler way to include values in strings: Write the value in parentheses, and write a backslash (\) before the parentheses. For example:”
    “let apples = 3
    let oranges = 5
    let appleSummary = "I have \(apples) apples."
    let fruitSummary = "I have \(apples + oranges) pieces of fruit.”
###### “Use three double quotes (""") for strings that take up multiple lines. Indentation at the start of each quoted line is removed, as long as it matches the indentation of the closing quote. For example:”
    let quotation = """
        Even though there's whitespace to the left,
        the actual lines aren't indented.
        Except for this line.
        Double quotes (") can appear without being escaped.
 
        I still have \(apples + oranges) pieces of fruit.
        """
###### “Create arrays and dictionaries using brackets ([]), and access their elements by writing the index or key in brackets. A comma is allowed after the last element.”
    //arrays
    “var shoppingList = ["catfish", "water", "tulips", "blue paint"]
    shoppingList[1] = "bottle of water"
    //dictionaries
    var occupations = [
        "Malcolm": "Captain",
        "Kaylee": "Mechanic",
    ]
    occupations["Jayne"] = "Public Relations”   
###### “To create an empty array or dictionary, use the initializer syntax.”
    “let emptyArray = [String]()
    let emptyDictionary = [String: Float]()”
###### “If type information can be inferred, you can write an empty array as [] and an empty dictionary as [:]—for example, when you set a new value for a variable or pass an argument to a function.”
    shoppingList = []
    occupations = [:]
##“Control Flow
##### Use if and switch to make conditionals, and use for-in, while, and repeat-while to make loops. Parentheses around the condition or loop variable are optional. Braces around the body are required.”
###### 使用if和switch来制作条件，并使用for-in，while和repeat-while来制作循环。 条件或循环变量周围的括号是可选的。 身体周围的{}是必需的。”
    “let individualScores = [75, 43, 103, 87, 12]
    var teamScore = 0
    for score in individualScores {
        if score > 50 {
            teamScore += 3
        } else {
            teamScore += 1
        }
    }
    print(teamScore)”
#####  “In an if statement, the conditional must be a Boolean expression—this means that code such as if score { ... } is an error, not an implicit comparison to zero.”
###### 注意：这里与OC中的if的使用是不一样的。
##### “You can use if and let together to work with values that might be missing. These values are represented as optionals. An optional value either contains a value or contains nil to indicate that a value is missing. Write a question mark (?) after the type of a value to mark the value as optional.”
    “var optionalString: String? = "Hello"
    print(optionalString == nil)
 
    var optionalName: String? = "John Appleseed"
    var greeting = "Hello!"
    if let name = optionalName {
        greeting = "Hello, \(name)"
    }”
##### “If the optional value is nil, the conditional is false and the code in braces is skipped. Otherwise, the optional value is unwrapped and assigned to the constant after let, which makes the unwrapped value available inside the block of code.”
###### “如果可选值为nil，则条件为false，并跳过大括号中的代码。 否则，可选值被解包并在let之后分配给常量，这使得在代码块内可用解包值。”
##### “Another way to handle optional values is to provide a default value using the ?? operator. If the optional value is missing, the default value is used instead.”
###### “处理可选值的另一种方法是使用??提供默认值。 如果缺少可选值，则使用默认值。”
    “let nickName: String? = nil
    let fullName: String = "John Appleseed"
    let informalGreeting = "Hi \(nickName ?? fullName)”
##### “Switches support any kind of data and a wide variety of comparison operations—they aren’t limited to integers and tests for equality.”
###### “Switches支持任何类型的数据和各种各样的比较操作 - 它们不仅限于整数和相等的数值。”
    “let vegetable = "red pepper"
    switch vegetable {
    case "celery":
        print("Add some raisins and make ants on a log.")
    case "cucumber", "watercress":
        print("That would make a good tea sandwich.")
    case let x where x.hasSuffix("pepper"):
        print("Is it a spicy \(x)?")
    default:
        print("Everything tastes good in soup.")
    }”
###### 讲真，第一次看到这个的时候，我是无比激动的。
###### “请注意如何在模式中使用let将模式匹配的值赋给常量。”
##### “After executing the code inside the switch case that matched, the program exits from the switch statement. Execution doesn’t continue to the next case, so there is no need to explicitly break out of the switch at the end of each case’s code.”
###### 就是说不用在每个case里面再添加break了。
##### “You use for-in to iterate over items in a dictionary by providing a pair of names to use for each key-value pair. Dictionaries are an unordered collection, so their keys and values are iterated over in an arbitrary order.”
###### “通过提供一对用于每个键值对的名称，您可以使用for-in来迭代字典中的项目。 字典是一个无序集合，因此它们的键和值以任意顺序迭代。”
    “let interestingNumbers = [
        "Prime": [2, 3, 5, 7, 11, 13],
        "Fibonacci": [1, 1, 2, 3, 5, 8],
        "Square": [1, 4, 9, 16, 25],
    ]
    var largest = 0
    for (kind, numbers) in interestingNumbers {
        for number in numbers {
            if number > largest {
                largest = number
            }
        }
    }
    print(largest)”
##### “Use while to repeat a block of code until a condition changes. The condition of a loop can be at the end instead, ensuring that the loop is run at least once.”
    “var n = 2
    while n < 100 {
        n *= 2
    }
    print(n)
     
    var m = 2
    repeat {
        m *= 2
    } while m < 100
    print(m)”
##### “You can keep an index in a loop by using ..< to make a range of indexes.”
    “var total = 0
    for i in 0..<4 {
        total += i
    }
    print(total)”
##### “Use ..< to make a range that omits its upper value, and use ... to make a range that includes both values.”

## Functions and Closures
##### “Use func to declare a function. Call a function by following its name with a list of arguments in parentheses. Use -> to separate the parameter names and types from the function’s return type.”
###### “使用func声明一个函数。 通过在括号中使用参数列表跟随其名称来调用函数。 使用 - >将参数名称和类型与函数的返回类型分开。”
    “func greet(person: String, day: String) -> String {
        return "Hello \(person), today is \(day)."
      }
      
     greet(person: "Bob", day: "Tuesday")”
##### “By default, functions use their parameter names as labels for their arguments. Write a custom argument label before the parameter name, or write _ to use no argument label.

    func greet(_ person: String, on day: String) -> String {
        return "Hello \(person), today is \(day)."
    }
    
    greet("John", on: "Wednesday")”
##### “Use a tuple to make a compound value—for example, to return multiple values from a function. The elements of a tuple can be referred to either by name or by number.”
    “func calculateStatistics(scores: [Int]) -> (min: Int, max: Int, sum: Int) {
        var min = scores[0]
        var max = scores[0]
        var sum = 0
        
        for score in scores {
            if score > max {
                max = score
            } else if score < min {
                min = score
            }
            sum += score
        }
        
        return (min, max, sum)
    }
    
    let statistics = calculateStatistics(scores: [5, 3, 100, 3, 9])
    print(statistics.sum)
    print(statistics.2)”
    
##### “Functions can be nested. Nested functions have access to variables that were declared in the outer function. You can use nested functions to organize the code in a function that is long or complex.

    func returnFifteen() -> Int {
        var y = 10
        func add() {
            y += 5
        }
        add()
        return y
    }
    returnFifteen()”
##### “Functions are a first-class type. This means that a function can return another function as its value.”
    “func makeIncrementer() -> ((Int) -> Int) {
        func addOne(number: Int) -> Int {
            return 1 + number
        }
        return addOne
    }
    var increment = makeIncrementer()
    increment(7)”
###### 是不是各种骚操作满天飞
##### “A function can take another function as one of its arguments.

    func hasAnyMatches(list: [Int], condition: (Int) -> Bool) -> Bool {
        for item in list {
            if condition(item) {
                return true
            }
        }
        return false
    }
    func lessThanTen(number: Int) -> Bool {
        return number < 10
    }
    var numbers = [20, 19, 7, 12]
    hasAnyMatches(list: numbers, condition: lessThanTen)”
##### “Functions are actually a special case of closures: blocks of code that can be called later. The code in a closure has access to things like variables and functions that were available in the scope where the closure was created, even if the closure is in a different scope when it is executed—you saw an example of this already with nested functions. You can write a closure without a name by surrounding code with braces ({}). Use in to separate the arguments and return type from the body.”
###### “函数实际上是闭包的一种特殊情况：可以在以后调用的代码块。 闭包中的代码可以访问创建闭包的作用域中可用的变量和函数，即使闭包在执行时的不同作用域 - 您已经看到了嵌套函数的示例。 您可以使用大括号（{}）来编写没有名称的闭包。 用于将参数和返回类型与正文分开。”
    “numbers.map({ (number: Int) -> Int in
        let result = 3 * number
        return result
    })”
    
##### “You have several options for writing closures more concisely. When a closure’s type is already known, such as the callback for a delegate, you can omit the type of its parameters, its return type, or both. Single statement closures implicitly return the value of their only statement.

    let mappedNumbers = numbers.map({ number in 3 * number })
    print(mappedNumbers)”
###### “你有几种选择来更简洁地编写闭包。 当已知闭包的类型（例如委托的回调）时，可以省略其参数的类型，返回类型或两者。 单个语句闭包隐式返回其唯一语句的值。
##### “You can refer to parameters by number instead of by name—this approach is especially useful in very short closures. A closure passed as the last argument to a function can appear immediately after the parentheses. When a closure is the only argument to a function, you can omit the parentheses entirely.

    let sortedNumbers = numbers.sorted { $0 > $1 }
    print(sortedNumbers)”
    
###### “您可以按编号而不是按名称来引用参数 - 这种方法在非常短的闭包中特别有用。 作为函数的最后一个参数传递的闭包可以在括号后面立即出现。 当闭包是函数的唯一参数时，可以完全省略括号。
## Objects and Classes
##### “Use class followed by the class’s name to create a class. A property declaration in a class is written the same way as a constant or variable declaration, except that it is in the context of a class. Likewise, method and function declarations are written the same way.”
    “class Shape {
        var numberOfSides = 0
        func simpleDescription() -> String {
            return "A shape with \(numberOfSides) sides."
        }
    }”
###### “使用类后跟类的名称来创建一个类。 类中的属性声明与常量或变量声明的编写方式相同，只是它位于类的上下文中。 同样，方法和函数声明也以相同的方式编写。”
##### “Create an instance of a class by putting parentheses after the class name. Use dot syntax to access the properties and methods of the instance.

    var shape = Shape()
    shape.numberOfSides = 7
    var shapeDescription = shape.simpleDescription()”
##### “This version of the Shape class is missing something important: an initializer to set up the class when an instance is created. Use init to create one.

    class NamedShape {
        var numberOfSides: Int = 0
        var name: String
        
        init(name: String) {
            self.name = name
        }
        
        func simpleDescription() -> String {
            return "A shape with \(numberOfSides) sides."
        }
    }”
##### “Notice how self is used to distinguish the name property from the name argument to the initializer. The arguments to the initializer are passed like a function call when you create an instance of the class. Every property needs a value assigned—either in its declaration (as with numberOfSides) or in the initializer (as with name).

##### Use deinit to create a deinitializer if you need to perform some cleanup before the object is deallocated.

##### Subclasses include their superclass name after their class name, separated by a colon. There is no requirement for classes to subclass any standard root class, so you can include or omit a superclass as needed.

##### 【Methods on a subclass that override the superclass’s implementation are marked with override—overriding a method by accident, without override, is detected by the compiler as an error. The compiler also detects methods with override that don’t actually override any method in the superclass.”】

    “class Square: NamedShape {
        var sideLength: Double
        
        init(sideLength: Double, name: String) {
            self.sideLength = sideLength
            super.init(name: name)
            numberOfSides = 4
        }
        
        func area() -> Double {
            return sideLength * sideLength
        }
        
        override func simpleDescription() -> String {
            return "A square with sides of length \(sideLength)."
        }
    }
    let test = Square(sideLength: 5.2, name: "my test square")
    test.area()
    test.simpleDescription()”


###### “注意self是如何用来区分name属性和name参数到初始化器的。创建类的实例时，初始化程序的参数就像函数调用一样传递。每个属性都需要一个赋值 - 在其声明中（与numberOfSides一样）或在初始化器中（与name一样）。

###### 如果需要在取消分配对象之前执行一些清理，请使用deinit创建一个deinitializer。

###### 子类在其类名后面包含它们的超类名称，用冒号分隔。类不需要子类化任何标准根类，因此您可以根据需要包含或省略超类。

###### 【覆盖超类的实现的子类上的方法标记为覆盖 - 覆盖方法意外，没有覆盖，编译器将其检测为错误。编译器还检测具有覆盖的方法，这些方法实际上不会覆盖超类中的任何方法。”】（这句话的理解，我水平有限，借助谷歌也就翻译成这样，如果大家能够很好的理解这段话，还烦请大家给我留言）
##### “In addition to simple properties that are stored, properties can have a getter and a setter.”
    “class EquilateralTriangle: NamedShape {
        var sideLength: Double = 0.0
        
        init(sideLength: Double, name: String) {
            self.sideLength = sideLength
            super.init(name: name)
            numberOfSides = 3
        }
        
        var perimeter: Double {
            get {
                return 3.0 * sideLength
            }
            set {
                sideLength = newValue / 3.0
            }
        }
        
        override func simpleDescription() -> String {
            return "An equilateral triangle with sides of length \(sideLength)."
        }
    }
    var triangle = EquilateralTriangle(sideLength: 3.1, name: "a triangle")
    print(triangle.perimeter)
    triangle.perimeter = 9.9
    print(triangle.sideLength)”
##### “In the setter for perimeter, the new value has the implicit name newValue. You can provide an explicit name in parentheses after set.”
###### “在set设置器中，新值具有隐含名称newValue。 您可以在设置后在括号中提供显式名称。”
##### “Notice that the initializer for the EquilateralTriangle class has three different steps:

##### Setting the value of properties that the subclass declares.
##### Calling the superclass’s initializer.
##### Changing the value of properties defined by the superclass. Any additional setup work that uses methods, getters, or setters can also be done at this point.”
##### “If you don’t need to compute the property but still need to provide code that is run before and after setting a new value, use willSet and didSet. The code you provide is run any time the value changes outside of an initializer. For example, the class below ensures that the side length of its triangle is always the same as the side length of its square.

    class TriangleAndSquare {
        var triangle: EquilateralTriangle {
            willSet {
                square.sideLength = newValue.sideLength
            }
        }
        var square: Square {
            willSet {
                triangle.sideLength = newValue.sideLength
            }
        }
        init(size: Double, name: String) {
            square = Square(sideLength: size, name: name)
            triangle = EquilateralTriangle(sideLength: size, name: name)
        }
    }
    var triangleAndSquare = TriangleAndSquare(size: 10, name: "another test shape")
    print(triangleAndSquare.square.sideLength)
    print(triangleAndSquare.triangle.sideLength)
    triangleAndSquare.square = Square(sideLength: 50, name: "larger square")
    print(triangleAndSquare.triangle.sideLength)”
###### “如果您不需要计算属性但仍需要提供在设置新值之前和之后运行的代码，请使用willSet和didSet。 您提供的代码在值在初始化程序之外更改时运行。 例如，下面的类确保其三角形的边长始终与其正方形的边长相同。
##### “When working with optional values, you can write ? before operations like methods, properties, and subscripting. If the value before the ? is nil, everything after the ? is ignored and the value of the whole expression is nil. Otherwise, the optional value is unwrapped, and everything after the ? acts on the unwrapped value. In both cases, the value of the whole expression is an optional value.
    
    let optionalSquare: Square? = Square(sideLength: 2.5, name: "optional square")
    let sideLength = optionalSquare?.sideLength”
###### “使用可选值时，在诸如方法，属性和下标之类的操作之前你可以写？。 如果？之前的值是零，那么？之后的所有值都被忽略，整个表达式的值为零。 否则，可选值解包，并且后面的一切都是？ 对未包装的价值采取行动。 在这两种情况下，整个表达式的值都是可选值。
## Enumerations and Structures
##### “Use enum to create an enumeration. Like classes and all other named types, enumerations can have methods associated with them.

    enum Rank: Int {
        case ace = 1
        case two, three, four, five, six, seven, eight, nine, ten
        case jack, queen, king
        func simpleDescription() -> String {
            switch self {
            case .ace:
                return "ace"
            case .jack:
                return "jack"
            case .queen:
                return "queen"
            case .king:
                return "king"
            default:
                return String(self.rawValue)
            }
        }
    }
    let ace = Rank.ace
    let aceRawValue = ace.rawValue”
##### “By default, Swift assigns the raw values starting at zero and incrementing by one each time, but you can change this behavior by explicitly specifying values. In the example above, Ace is explicitly given a raw value of 1, and the rest of the raw values are assigned in order. You can also use strings or floating-point numbers as the raw type of an enumeration. Use the rawValue property to access the raw value of an enumeration case.

##### Use the init?(rawValue:) initializer to make an instance of an enumeration from a raw value. It returns either the enumeration case matching the raw value or nil if there is no matching”

    if let convertedRank = Rank(rawValue: 3) {
        let threeDescription = convertedRank.simpleDescription()
    }”
##### “The case values of an enumeration are actual values, not just another way of writing their raw values. In fact, in cases where there isn’t a meaningful raw value, you don’t have to provide one.
    
    enum Suit {
        case spades, hearts, diamonds, clubs
        func simpleDescription() -> String {
            switch self {
            case .spades:
                return "spades"
            case .hearts:
                return "hearts"
            case .diamonds:
                return "diamonds"
            case .clubs:
                return "clubs"
            }
        }
    }
    let hearts = Suit.hearts
    let heartsDescription = hearts.simpleDescription()”
###### 不一定设置原始值
##### “Notice the two ways that the hearts case of the enumeration is referred to above: When assigning a value to the hearts constant, the enumeration case Suit.hearts is referred to by its full name because the constant doesn’t have an explicit type specified. Inside the switch, the enumeration case is referred to by the abbreviated form .hearts because the value of self is already known to be a suit. You can use the abbreviated form anytime the value’s type is already known.”
##### “If an enumeration has raw values, those values are determined as part of the declaration, which means every instance of a particular enumeration case always has the same raw value. Another choice for enumeration cases is to have values associated with the case—these values are determined when you make the instance, and they can be different for each instance of an enumeration case. You can think of the associated values as behaving like stored properties of the enumeration case instance. For example, consider the case of requesting the sunrise and sunset times from a server. The server either responds with the requested information, or it responds with a description of what went wrong.

    enum ServerResponse {
        case result(String, String)
        case failure(String)
    }
     
    let success = ServerResponse.result("6:00 am", "8:09 pm")
    let failure = ServerResponse.failure("Out of cheese.")
     
    switch success {
    case let .result(sunrise, sunset):
        print("Sunrise is at \(sunrise) and sunset is at \(sunset).")
    case let .failure(message):
        print("Failure...  \(message)")
    }”
###### “如果枚举具有原始值，则这些值将作为声明的一部分确定，这意味着特定枚举情况的每个实例始终具有相同的原始值。枚举情况的另一个选择是使值与案例相关联 - 这些值在您创建实例时确定，并且对于枚举案例的每个实例它们可以不同。您可以将关联值视为与枚举案例实例的存储属性相似。例如，考虑从服务器请求日出和日落时间的情况。服务器响应所请求的信息，或者响应错误的描述。
##### “Notice how the sunrise and sunset times are extracted from the ServerResponse value as part of matching the value against the switch cases.

##### Use struct to create a structure. Structures support many of the same behaviors as classes, including methods and initializers. One of the most important differences between structures and classes is that structures are always copied when they are passed around in your code, but classes are passed by reference.”
    “struct Card {
        var rank: Rank
        var suit: Suit
        func simpleDescription() -> String {
            return "The \(rank.simpleDescription()) of \(suit.simpleDescription())"
        }
    }
    let threeOfSpades = Card(rank: .three, suit: .spades)
    let threeOfSpadesDescription = threeOfSpades.simpleDescription()”
## Protocols and Extensions
#####“Use protocol to declare a protocol.

    protocol ExampleProtocol {
        var simpleDescription: String { get }
        mutating func adjust()
    }
##### Classes, enumerations, and structs can all adopt protocols.

    class SimpleClass: ExampleProtocol {
        var simpleDescription: String = "A very simple class."
        var anotherProperty: Int = 69105
        func adjust() {
            simpleDescription += "  Now 100% adjusted."
        }
    }
    var a = SimpleClass()
    a.adjust()
    let aDescription = a.simpleDescription
     
    struct SimpleStructure: ExampleProtocol {
        var simpleDescription: String = "A simple structure"
        mutating func adjust() {
            simpleDescription += " (adjusted)"
        }
    }
    var b = SimpleStructure()
    b.adjust()
    let bDescription = b.simpleDescription”
##### “Notice the use of the mutating keyword in the declaration of SimpleStructure to mark a method that modifies the structure. The declaration of SimpleClass doesn’t need any of its methods marked as mutating because methods on a class can always modify the class.

###### “请注意，在SimpleStructure声明中使用mutating关键字来标记修改结构的方法。 SimpleClass的声明不需要任何标记为变异的方法，因为类上的方法总是可以修改类。

##### Use ext    ension to add functionality to an existing type, such as new methods and computed properties. You can use an extension to add protocol conformance to a type that is declared elsewhere, or even to a type that you imported from a library or framework.”
    “extension Int: ExampleProtocol {
        var simpleDescription: String {
            return "The number \(self)"
        }
        mutating func adjust() {
            self += 42
        }
    }
    print(7.simpleDescription)”

###### 使用扩展向现有类型添加功能，例如新方法和计算属性。 您可以使用扩展来将协议一致性添加到在其他地方声明的类型，甚至是从库或框架中导入的类型。”
##### “You can use a protocol name just like any other named type—for example, to create a collection of objects that have different types but that all conform to a single protocol. When you work with values whose type is a protocol type, methods outside the protocol definition are not available.
    let protocolVlet protocolValue: ExampleProtocol = a
    print(protocolValue.simpleDescription)
    // print(protocolValue.anotherProperty)  
    // Uncomment to see the error
###### “您可以像使用任何其他命名类型一样使用协议名称 - 例如，创建具有不同类型但都符合单个协议的对象集合。 使用类型为协议类型的值时，协议定义之外的方法不可用。
##### Even though the variable protocolValue has a runtime type of SimpleClass, the compiler treats it as the given type of ExampleProtocol. This means that you can’t accidentally access methods or properties that the class implements in addition to its protocol conformance.”
###### 即使变量protocolValue具有SimpleClass的运行时类型，编译器也会将其视为给定类型的ExampleProtocol。 这意味着除了协议一致性之外，您不会意外地访问该类实现的方法或属性。”
## Error Handling
##### “You represent errors using any type that adopts the Error protocol.”
    “enum PrinterError: Error {
       case outOfPaper
       case noToner
       case onFire
    }”
##### “Use throw to throw an error and throws to mark a function that can throw an error. If you throw an error in a function, the function returns immediately and the code that called the function handles the error.”
    “func send(job: Int, toPrinter printerName: String) throws -> String {
        if printerName == "Never Has Toner" {
            throw PrinterError.noToner
        }
        return "Job sent"
    }”
##### “There are several ways to handle errors. One way is to use do-catch. Inside the do block, you mark code that can throw an error by writing try in front of it. Inside the catch block, the error is automatically given the name error unless you give it a different name.”
    “do {
        let printerResponse = try send(job: 1040, toPrinter: "Bi Sheng")
        print(printerResponse)
    } catch {
        print(error)
    }”
##### “You can provide multiple catch blocks that handle specific errors. You write a pattern after catch just as you do after case in a switch.”
    “do {
        let printerResponse = try send(job: 1440, toPrinter: "Gutenberg")
        print(printerResponse)
    } catch PrinterError.onFire {
        print("I'll just put this over here, with the rest of the fire.")
    } catch let printerError as PrinterError {
        print("Printer error: \(printerError).")
    } catch {
        print(error)
    }”
##### “Another way to handle errors is to use try? to convert the result to an optional. If the function throws an error, the specific error is discarded and the result is nil. Otherwise, the result is an optional containing the value that the function returned.”
    “let printerSuccess = try? send(job: 1884, toPrinter: "Mergenthaler")
    let printerFailure = try? send(job: 1885, toPrinter: "Never Has Toner")”
###### “处理错误的另一种方法是使用try？ 将结果转换为可选。 如果函数抛出错误，则丢弃特定错误，结果为nil。 否则，结果是一个可选的，包含函数返回的值。”
##### “Use defer to write a block of code that is executed after all other code in the function, just before the function returns. The code is executed regardless of whether the function throws an error. You can use defer to write setup and cleanup code next to each other, even though they need to be executed at different times.”
    “var fridgeIsOpen = false
    let fridgeContent = ["milk", "eggs", "leftovers"]
     
    func fridgeContains(_ food: String) -> Bool {
        fridgeIsOpen = true
        defer {
            fridgeIsOpen = false
        }
        
        let result = fridgeContent.contains(food)
        return result
    }
    fridgeContains("banana")
    print(fridgeIsOpen)”
###### “使用defer编写一个代码块，该代码块在函数中的所有其他代码之后执行，就在函数返回之前。 无论函数是否抛出错误，都会执行代码。 你可以使用defer来编写彼此相邻的设置和清理代码，即使它们需要在不同的时间执行。”
## Generics
##### “Write a name inside angle brackets to make a generic function or type.

    func makeArray<Item>(repeating item: Item, numberOfTimes: Int) -> [Item] {
        var result = [Item]()
        for _ in 0..<numberOfTimes {
            result.append(item)
        }
        return result
    }
    makeArray(repeating: "knock", numberOfTimes: 4)”
##### “You can make generic forms of functions and methods, as well as classes, enumerations, and structures.

    // Reimplement the Swift standard library's optional type
    enum OptionalValue<Wrapped> {
        case none
        case some(Wrapped)
    }
    var possibleInteger: OptionalValue<Int> = .none
    possibleInteger = .some(100)”
##### “Use where right before the body to specify a list of requirements—for example, to require the type to implement a protocol, to require two types to be the same, or to require a class to have a particular superclass.
    
    func anyCommonElements<T: Sequence, U: Sequence>(_ lhs: T, _ rhs: U) -> Bool
        where T.Iterator.Element: Equatable, T.Iterator.Element == U.Iterator.Element {
            for lhsItem in lhs {
                for rhsItem in rhs {
                    if lhsItem == rhsItem {
                        return true
                    }
                }
            }
            return false
    }
    anyCommonElements([1, 2, 3], [3])”
    
##### “Writing <T: Equatable> is the same as writing <T> ... where T: Equatable.”
