# HackingWithSwift-

Hacking With Swift 这套教程的基础部分学习笔记
[Hacking with Swift](https://www.hackingwithswift.com/) 是由 [Paul Hudson](https://twitter.com/twostraws) 发布的 免费 Swift 教程，其涵盖了30个项目，并且包含了 Swift 2.0。因为该教程是面向初学者，所以很多知识点都没有深入探讨，如果想要深入学习可以参考官方文档：[The Swift Programming Language (Swift 2.1)](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/index.html#//apple_ref/doc/uid/TP40014097-CH3-ID0)<!--more-->

# Introducing to Swift
- Playground 是自 Xcode6 起苹果加入的实时浏览代码结果的一个功能。

<br />

- 变量通过 var 声明，常量通过 let 声明。
Swift 可以推断变量的类型(type reference)，所以声明变量可以直接如下：

{% codeblock lang:swift %}
var string = “My string”

//也可以先声明类型（必须）或声明与赋值同时：

var string:String = “My string”
{% endcodeblock %}


- 苹果官方建议在声明有小数部分的变量时都采用 Double，因其具有更高的精准度。

<br />

- Swift 中 bool 值是 true 和 false。

<br />

- “+” 号也可用于 string :

{% codeblock lang:swift %}
var name1 = "Tim McGraw"
var name2 = "Romeo"
var both = name1 + " and " + name2 //"Tim McGraw and Romeo"
{% endcodeblock %}


- 字符串的对比运算是”case-sensitive”，也就是区分大小写：

{% codeblock lang:swift %}
var name = “TIM MCGRAW" 
var name2 =  "TiM mCgRaW"
name == name2  //result is false
{% endcodeblock %}


- 在 string 中插入变量：

{% codeblock lang:swift %}
var name = “Tim McGraw”
“Your name is \(name)”
//可以在括号中运算：
var age = 25
“His age is \(age * 2)”
{% endcodeblock %}

##Arrays,Dictionaries,Loops,Switch case

- 通过类型注释（Type annotaions）可以申明数组内容的类型：

{% codeblock lang:swift %}
var songs: [String] = ["Shake it Off", "You Belong with Me", "Back to December", 3]
//以上会报错，因为数组内有非 String 类型的”3”在内。
{% endcodeblock %}

<br />

- 以下代码仅仅是声明了一个将要被分配包含String对象数组的变量：

{% codeblock lang:swift %}
var array:[String]
//没有真正创建数组对象

var array: [String] = []
//这时才是创建了数组对象

var array = [String] ()
//效果同上，语法更为简洁。
{% endcodeblock %}


- 数组可以直接使用”+”运算符结合：

{% codeblock lang:swift %}
var songs = ["Shake it Off", "You Belong with Me", "Love Story"]
var songs2 = ["Today was a Fairytale", "White Horse", "Fifteen"]
var both = songs + songs2

both += [“Everything”]
//可以增加并赋值
{% endcodeblock %}

<br />

- 创建一个 Disctionary：
 
{% codeblock lang:swift %}
var person = [
		"first": "Taylor",
		"middle": "Alison",
		"last": "Swift",
		"month": "December",
		"website": "taylorswift.com"
            ]
{% endcodeblock %}

            
- Swift 中，条件表达式不需要括号：
{% codeblock lang:swift %}
	if person == "hater" {
    	action = "hate"
	} else if person == "player" {
    	action = "play"
	} else {
    	action = "cruise"
	}
{% endcodeblock %}

		
- `在 Swift 2.0中，println() 改为 print()`

<br />

- Swift 的 for 循环语法：

{% codeblock lang:swift %}
// closed range operator
for i in 1...10{
	println("\(i) x 10 is \(i * 10)")
}
/*
以上结果相当于：
println("1 x 10 is \(1 * 10)")
println("2 x 10 is \(2 * 10)")
println("3 x 10 is \(3 * 10)")
println("4 x 10 is \(4 * 10)")
println("5 x 10 is \(5 * 10)")
println("6 x 10 is \(6 * 10)")
println("7 x 10 is \(7 * 10)")
println("8 x 10 is \(8 * 10)")
println("9 x 10 is \(9 * 10)")
println("10 x 10 is \(10 * 10)")
*/
{% endcodeblock %}

		
- 不需要「循环数」时也可以用下划线代替：

{% codeblock lang:swift %}
for _ in 1 ... 5 {
    str += " fake"
}
{% endcodeblock %}

-  half open range operator(半开区间运算符):"..<"，例如 ..<5 将会循环四次，count 将会是 1,2,3,4。"..<" 可以方便于遍历数组（数组的 index 从0算起）：

{% codeblock lang:swift %}
for i in 0 ..< count(people) {
    println("\(people[i]) gonna \(actions[i])")
}
{% endcodeblock %}


-  遍历数组的语法：

{% codeblock lang:swift %}
...
		
for song in songs {
    println("My favorite song is \(song)")
}
//通过 index 同时遍历俩数组：
var people = ["players", "haters", "heart-breakers", "fakers"]
var actions = ["play", "hate", "break", "fake"]

for i in 0 ... 3 {
    println("\(people[i]) gonna \(actions[i])")
		}
{% endcodeblock %}

<br />
		
- `获取数组内的对象数量的方法在 Swift 1.2中是 count(array)，在 Swift 2.0中是 array.count。`

<br />

- loop 中的 continue 语法 将会终止当前的迭代回到 loop 的开头继续迭代。

<br />

- switch/case 语法可以简化较多的 if/else if 语法，Swift 要求 switch 条件变量所有可能的情况都得涵盖（
cases should exhustive），否则 Xcode 可能无法构建应用，default 可以避免该问题。

<br />

- 可以在 switch/case 中使用 "..."(half open range operator) 将变量可能的范围作为一个 case：

{% codeblock lang:swift %}
let studioAlbums = 5
	switch studioAlbums {
		case 0...1:
    		println("You're just starting out")
		case 2...3:
    		println("You're a rising star")
		case 4...5:
    		println("You're world famous!")
		default:
    		println("Have you done something new?")
		}
{% endcodeblock %}


- `Swift 2.0 方法调用和1.2稍有不同，需要写明参数名，目的是提高代码可读性：`

{% codeblock lang:swift %}
func printAlbumRelease(name: String, year: Int) {
    println("\(name) was released in \(year)")
}
printAlbumRelease("Fearless", year: 2008)
printAlbumRelease("Speak Now", year: 2010)
printAlbumRelease("Red", year: 2012)
{% endcodeblock %}

		
- "->"符号为方法声明返回值：
{% codeblock lang:swift %}
func albumsIsTaylor(name: String) -> Bool 
{% endcodeblock %}


##Optionals
<br />
Apple 在 Swift 中为其加入了 Optional，Optional 是一种类型，可以有值，也可以等于 nil（也就是没有值）。在 oc 中，只有指向对象的指针可以为 nil，而在 swift 中基本类型创建后没有初始值，而是为 nil，并且无法使用。

开发中遇到的一些意想不到的问题，例如程序崩溃、影响UI,最常见的原因就是因为使用了为 nil 的值，Optional 这一特性确保了代码安全性。

- 定义一个 Optional 的值只需在类型后添加一个问号“?”：
 
{% codeblock lang:swift %}
var str: String? //输出nil
		
//以上是一个名为 str 的 Optional String.
{% endcodeblock %}

- Optional 类型无法直接使用，需要拆包(unwrap)后取出原类型的值后使用。在 Optional 类型后加上感叹号(!)进行显式拆包（Force unwrapping optionals）：
		
{% codeblock lang:swift %}
var str: String? = "Hallo World"
		
str  //nil
str!  //"Hallo World"
		
print(str) //输出"Optional("Hallo World")"
print(str!) //输出"Hallo World"
{% endcodeblock %}


- 通过 if let 语句可以判断 Optional 是否有值，如果有，将其拆包赋值给一个本地变量：

{% codeblock lang:swift %}
func getHaterStatus(weather: String) -> String? {
    if weather == "sunny" {
        return nil
    } else {
        return "Hate"
    }
    //该方法返回一个 Optional String 类型
}

func takeHaterAction(status: String) {
    if status == "Hate" {
        print("Hating")
    }
    //该方法需要传入一个 String 类型
}

if let status = getHaterStatus("rainy") {
    takeHaterAction(status)
    		
/* if let 语句将调用了 getHaterStatus 方法后得到的 Optional 值拆包后赋值给本地变量 status，确保 takeHaterAction 方法传入的是一个有值的参数。 */
} 
{% endcodeblock %}

<br />

- Optional 还提供了隐式拆包（implicitly unwrapped optionals），隐式拆包的 Optional 在使用前无需拆包。要使用隐式拆包需要在变量声明时的数据类型后加上感叹号(!)：

{% codeblock lang:swift %}
var str: String! = "Hello World!"
str //Hello World!
{% endcodeblock %}

		
使用隐式拆包需要小心，要确保变量已被正确初始化。一般会在以下情况遇到 Implicitly unwrapped：

1. 当使用 Apple 的 API 时会经常碰到隐式拆包的返回值。
2. 当使用 UIKit 的用户界面元素时。


###总结一下 Optional：
<br />

- 一个普通类型的变量必须有值，比如一个 String 变量需要拥有一个 string，哪怕是空的字符串（"")。

- 一个 Optional 类型的变量可以有值也可以无值（也就是为nil），但在使用前必须将其拆包(Unwrap)。

- 一个隐式拆包的 Optional 类型变量可以有值也可以无值，使用前不需要拆包，因此 Swift 也不会为你检查，需要格外小心。

<br />

----------------------------------

<br />

- Optional Chaining：
在 Objective-C 中，对 nil 发送消息会得到 nil，但是在 Swift 中不允许这么做。当对一个 Optional 类型的对象发送消息时，通过 Optional Chaining 可以对其判断是否有值，如果是则发送消息，反之则什么也不做：
		
{% codeblock lang:swift %}
func albumReleasedYear(year: Int) -> String? {
    switch year {
    case 2006: return "Taylor Swift"
    case 2008: return "Fearless"
    case 2010: return "Speak Now"
    case 2012: return "Red"
    case 2014: return "1989"
    default: return nil
    }
}

let album = albumReleasedYear(2006)?.uppercaseString //输出 Optional("TAYLOR SWFIT")
//即问号(?)前有值才发送消息，这就是 Optional Chaining

Optional Chaining 如同其名可以像链条一样连接，多长都可以，Swift 会从左至右检查直至发现 nil 即终止：
		
let album = albumReleasedYear(2006)?.someOptionalValue?.someOtherOptionalValue?.whatever
{% endcodeblock %}

<br />

- The nil coalescing operator：
Swift 的这个特性可以让你的代码更加简单和安全。例如：当 Value A 有值时则使用 Value A，如果 Value A 无值，则使用 Value B，这对 Optional 十分有用：

{% codeblock lang:swift %}
let album = albumReleasedYear(2006) ?? "unknown"
print("The album is \(album)")
//如果 albumReleasedYear(2006)返回的 Optional 无值，则使用非 Optional "unknown".
{% endcodeblock %}

<br />

##Enumeration
<br />
- 枚举（Enum）可以将一系列相关的值定义为一个组类型，通过如下语法创建 enum：

{% codeblock lang:swift %}
enum WeatherType {
	case Sun, Cloud, Rain, Wind, Snow
}
{% endcodeblock %}
	
下面看看如何使用枚举类型：

{% codeblock lang:swift %}
func getHaterStatus(weather: WeatherType) -> String? {
    if weather == WeatherType.Sun {
        return nil
    } else {
        return "Hate"
    }
}

getHaterStatus(WeatherType.Cloud)
{% endcodeblock %}

也可以这么定义枚举：

{% codeblock lang:swift %}
enum WeatherType {
    case Sun
    case Cloud
    case Rain
    case Wind
    case Snow
}
{% endcodeblock %}

也可以这么使用枚举：

{% codeblock lang:swift %}
func getHaterStatus(weather: WeatherType) -> String? {
    if weather == .Sun {
        return nil
    } else {
        return "Hate"
    }
}
	//Swift 通过 Type inference 知道你与 WeatherType 类型比较，所以无需写明枚举类型，但是这种写法 Swift 将不会提供代码补足建议辅助

getHaterStatus(.Cloud)
{% endcodeblock %}

<br />

枚举在 switch/case 中十分有用，因为 Swfit 知道你的枚举类型中都都有什么值，所以能确保你涵盖了所有的 case：

{% codeblock lang:swift %}
func getHaterStatus(weather: WeatherType) -> String? {
    switch weather {
    case .Sun:
        return nil
    case .Cloud, .Wind:
        return "dislike"
    case .Rain:
        return "hate"
    }
    //这段代码不会成功编译，应该添加 case .Snow 或是 default case。
}
{% endcodeblock %}

对于 Enum，Swift 还有一个非常强大的特性：可以为组中的值再附加一个值，进一步细分：

{% codeblock lang:swift %}
enum WeatherType {
    case Sun
    case Cloud
    case Rain
    case Wind(speed: Int)
    case Snow
}
{% endcodeblock %}

如此，使用 switch/case 时就有了额外的条件，当条件都满足时 case 才会匹配：

{% codeblock lang:swift %}
func getHaterStatus(weather: WeatherType) -> String? {
    switch weather {
    case .Sun:
        return nil
    case .Wind(let speed) where speed < 10: //meh
        return "meh"
    case .Cloud, .Wind:
        return "dislike"
    case .Rain, .Snow:
        return "hate"
    }
}

getHaterStatus(WeatherType.Wind(speed: 5))
{% endcodeblock %}

代码段第五行的 let 关键字的用途是声明一个能引用的常量名保存传入的参数，通过 Where 关键字来声明条件。

Swift 从上至下判断 switch/case 语句，所以请注意 case 的排序。

##Structs
Structs（结构体） 是一种复杂数据类型，包含了多个值，通过 struct 关键字定义一个结构体：

{% codeblock lang:swift %}
struct Person {
    var clothes: String
    var shoes: String
}
{% endcodeblock %}

Swift 让你非常简单地创建一个结构体变量，只需要将初始值传入即可：

{% codeblock lang:swift %}
let taylor = Person(clothes: "T-shirt", shoes: "sneakers")
let other = Person(clothes: "short skirts, shoes: "high heels")
{% endcodeblock %}

通过结构体变量名以及属性名来访问属性的值：

{% codeblock lang:swift %}
print(taylor.clothes)
print(other.shoes)
{% endcodeblock %}

Swift 有一个名为"copy on write"的机制，当你将一个结构体变量赋给另一个变量时，会独立拷贝一份：

{% codeblock lang:swift %}
struct Person {
    var clothes: String
    var shoes: String
}

let taylor = Person(clothes: "T-shirts", shoes: "sneakers")
let other = Person(clothes: "short skirts", shoes: "high heels")

var taylorCopy = taylor
taylorCopy.shoes = "flip flops"

taylor       //(clothes: "short skirts", shoes: "high heels")
taylorCopy   //(clothes: "short skirts", shoes: "flip flops")
{% endcodeblock %}

##Classes
通过 class 关键字定义一个类：

{% codeblock lang:swift %}
class Person {
    var clothes: String
    var shoes: String
}
{% endcodeblock %}

但是上面有个问题，Swift 不允许创建未被正确初始化的变量。解决方法有三种：

1. 将这两个变量定义为 Optional。（这会致使代码中出现大量不必要的 Optional 类型）
2. 给变量附上一个初始值。（这行得通，但这有点浪费，除非这个初始值一定会被使用）
3. 自己写一个初始化方法。（最佳）

通过创建一个 init() 方法来实现自定义初始化方法：

{% codeblock lang:swift %}
class Person {
    var clothes: String
    var shoes: String

   init(clothes: String, shoes: String) {
        self.clothes = clothes
        self.shoes = shoes
        //init方法不需要添加 func 关键字
    }
}
{% endcodeblock %}

实例化一个类：

{% codeblock lang:swift %}
var taylor = Person(name: "Taylor", age: 25)
{% endcodeblock %}

继承一个类：

{% codeblock lang:swift %}
class Singer: Person {

}
{% endcodeblock %}

在 Swift 中，想要在继承类（子类）中覆盖父类的方法，需要使用 override 关键字：

class Singer: Person {
    override func sing() {
        print("Trucks, girls, and liquor")
    }
}

通过 super 关键字调用父类方法：

{% codeblock lang:swift %}
    init(name: String, age: Int, noiseLevel: Int) {
        self.noiseLevel = noiseLevel
        super.init(name: name, age: age)
    }
{% endcodeblock %}

- 在 Swift 中，类和结构体有点相似，都可以拥有属性和方法，区别在于结构体是值拷贝，这意味着改变拷贝值不会改变原来的值，而类是指针拷贝，拷贝的变量会指向相同的实例，见下例：

{% codeblock lang:swift %}
// Value type example
struct S { var data: Int = -1 }
var a = S()
var b = a                        // a is copied to b
a.data = 42                        // Changes a, not b
println("\(a.data), \(b.data)")    // prints "42, -1"

// Reference type example
class C { var data: Int = -1 }
var x = C()
var y = x                        // x is copied to y
x.data = 42                        // changes the instance referred to by x (and y)
println("\(x.data), \(y.data)")    // prints "42, 42"
{% endcodeblock %}


##Properties
结构体和类（统称为 types）可以拥有自己的变量和常量（统称为 properties）。types 也可拥有方法来处理 properties：

{% codeblock lang:swift %}
struct Person {
   var clothes: String
   var shoes: String
	
   func describe() {
		print("I like wearing \(clothes) with \(shoes)")
	} 
}

let taylor = Person(clothes: "T-shirts", shoes: "sneakers")
let other = Person(clothes: "short skirts", shoes: "high heels")
taylor.describe() //"I like wearing T-shirts with sneakers"
other.describe() //"I like wearing short skirts with high heels"
//调用方法时，不同的对象使用相应的值
{% endcodeblock %}


###Property observers
Swift 提供了两个观察者方法，willSet 和 didSet，分别会在属性的值将要改变以及改变后触发（常用于用户界面的更新）：

{% codeblock lang:swift %}
struct Person {
    var clothes: String {
        willSet { 
            updateUI("I'm changing from \(clothes) to \(newValue)")
        }
        didSet {
            updateUI("I just changed from \(oldValue) to \(clothes)")
        }
    }
}

func updateUI(msg: String) {
    print(msg)
}

var taylor = Person(clothes: "T-shirts")
taylor.clothes = "short skirts" //值改变，将会调用观察者方法
{% endcodeblock %}

###Computed properties
Computed properties 其实就是自己重写属性的 get/set 方法：

{% codeblock lang:swift %}
struct Person {
   var age: Int

   var ageInDogYears: Int {
        get {
            return age * 7
        }
    }
}

var fan = Person(age: 25)
print(fan.ageInDogYears) //输出：25 * 7
{% endcodeblock %}

###Static properties and methods
静态属性和方法属于 type（class\struct），而不属于类的实例，这可以更好的组织一个共享的储存数据。通过 static 关键字声明一个静态变量：

{% codeblock lang:swift %}
struct TaylorFan {
    static var favoriteSong = "Shake it Off"

   var name: String
   var age: Int
}

let fan = TaylorFan(name: "James", age: 25)
print(TaylorFan.favoriteSong)
//每个 TaylorFan 类型的对象都会有自己的名字和年龄，但他们都有共同喜欢的歌曲："Shake it Off"
{% endcodeblock %}

<br />

因为静态属性和方法存在于 类 中，所以静态方法是无法访问非静态属性的。

##Access control
在 Xcode beta4 中 Swift 增加了这个特性，Access control 让你明确在结构体、类中的数据该怎么面向外界，有以下三种关键字：

- Public：所有人都可以读写属性。
- Internal：这是默认访问级别，模块中的 swift 代码都可以访问。
- Private：只有当前Swift源文件可以访问。

大多数时候你不必明确访问级别，但有些时候你会需要将一个属性设为`private`，使其无法被其他人直接访问。
这样声明一个 private 的属性：

{% codeblock lang:swift %}
class TaylorFan {
    private var name: String!
}
{% endcodeblock %}

注意：Playground 不受 Access control 的限制，因为它可以无碍地访问文件因此它可以读写任何数据。

##Polymorphism and type casting

Polymorphism 译为多态，指的是在类的继承中，子类会继承父类的属性、方法，多态即指子类可以拥有父类或自身定义的两种行为，你可以为其选择：

{% codeblock lang:swift %}
class Album {
   var name: String

   init(name: String) {
        self.name = name
    }
}

class StudioAlbum: Album {
   var studio: String

   init(name: String, studio: String) {
        self.studio = studio
        super.init(name: name)
    }
}

class LiveAlbum: Album {
   var location: String

   init(name: String, location: String) {
        self.location = location
        super.init(name: name)    //子类调用父类方法，实现父类的行为
    }
}
{% endcodeblock %}

当子类想要实现自己的行为时，可以通过 `override`关键字 重写 父类方法，如此将会实现子类自己定义的方法行为：

{% codeblock lang:swift %}
class LiveAlbum: Album {
    var location: String

   init(name: String, location: String) {
        self.location = location
        super.init(name: name)
    }

   override func getPerformance() -> String {
        return "The live album \(name) sold lots"
    }
}
{% endcodeblock %}

总而言之，一个对象可以同时实现自己类的行为和其父类的行为，这称为「多态」。

###Converting types with type casting
这种情况时有发生：你有一个明确声明的对象，但你知道它其实是另一种类型（比如上面的继承类StudioAlbum 和 LiveAlbum 被当做 Album 保存在数组中，因为它们继承于 Album 所以是允许的），当需要调用方法时，Swift 可能不知道它的真实类型而无法编译，解决办法是 type casting，即类型转换，可以将一个对象的类型转为另一种类型：

{% codeblock lang:swift %}
for album in allAlbums {
    print(album.getPerformance())
} //根据上面代码块的内容
{% endcodeblock %}

`allAlbums` 数组拥有三个类型为 `Album` 的对象，但是其中两个我们知道是 `StudioAlbum` 和 `LiveAlbum`，但是 Swift 却不知道，如果你想执行 `print(album.studio)` 则无法编译，因为只有 `StudioAlbum`拥有那个属性。

Type casting 有三种形式，但常见的只有两种：`as?` 和 `as!`，分别是可选向下转型以及强制向下转型，前者会返回一个转型后的可选值（optional value），若转型失败会返回nil；当你确定可以转型成功时使用后者，如果转型失败可能导致应用崩溃：
*P.S.「转型」并不是指真的改变实例或它的值，而只是告诉 Swift 把这个对象看做某个类的实例。*

{% codeblock lang:swift %}
for album in allAlbums {
    let studioAlbum = album as? StudioAlbum
} 
{% endcodeblock %}

studioAlbum 变量将会拥有一个StudioAlbum？类型数据或是nil，这经常与`if let`配合使用来自动解包 optional 值：

{% codeblock lang:swift %}
for album in allAlbums {
   print(album.getPerformance())

   if let studioAlbum = album as? StudioAlbum {
        print(studioAlbum.studio)
   } else if let liveAlbum = album as? LiveAlbum {
        print(liveAlbum.location)
   }
}
{% endcodeblock %}

遍历 allAlums 数组内的对象，并判断它们是否为特定子类，如果是，调用子类的方法/属性。

强制向下转型（forced downcasting）就相当于转型并强制拆包，返回的是一个非 optional 值，可以直接使用：

{% codeblock lang:swift %}
var taylorSwift = StudioAlbum(name: "Taylor Swift", studio: "The Castles Studios")
var fearless = StudioAlbum(name: "Speak Now", studio: "Aimeeland Studio")

var allAlbums: [Album] = [taylorSwift, fearless]

for album in allAlbums {
    let studioAlbum = album as! StudioAlbum
    print(studioAlbum.studio)
	//便利数组时如果数组内有 liveAlbum 类的实例就会 crash，因为使用了强制转型
	//所以为了不 crash，只存放 `StudioAlbum` 实例在数组中
}
{% endcodeblock %}

Swfit 也允许将转型写在数组遍历层，在数组便利初始就将数据转型，如此更有效率：

{% codeblock lang:swift %}
for album in allAlbums as! [StudioAlbum] {
    print(album.studio) //相当于省去了 let studioAlbum = album as! StudioAlbum
}
{% endcodeblock %}

但这么用必须得确保数组中所有实例都是 StudioAlbum 类型，否则会crash。

可选向下转型（optional downcasting）也可以这么用，但因为这样做有可能提供给「遍历」一个nil，所以需要用 ??(nil coalescing operator) 来确保提供给 loop 一个值：

{% codeblock lang:swift %}
for album in allAlbums as? [LiveAlbum] ?? [LiveAlbum]（）) {
    print(album.location)
}
{% endcodeblock %}

这样相当于：尝试将对象从 `allAlbums` 转为 `LiveAlbum` 类型，如果失败，就创建一个空的 `LiveAlbum` 对象来替代，这相当于啥也没做。这有可能会用得上，不过最好不这么做。

##Closures
闭包（Closures）相当于 OC 中的 blocks，是包含一段代码的变量，闭包在 Cocoa Touch 中很常见。和方法（function）不同的是，闭包是变量，可以作为参数传递或是作为属性（property）储存。下面看例子：

{% codeblock lang:swift %}
let vw = UIView()

UIView.animateWithDuration(0.5, animations: {
    vw.alpha = 0
})
{% endcodeblock %}

UIView 的 animateWithDuration 方法要求传入一个内含动画内容的闭包，其他的 Cocoa Touch 会帮你实现。之所以要使用闭包作为参数是因为 UIKit 在执行动画前需要做些准备，如此它会拷贝一份闭包内的代码并且在准备完成后执行。
以上示例也显示出在闭包内可以使用其外部的变量，这个特性成为闭包捕获。在闭包外声明了 vw 变量，并在闭包中使用了它。这十分有用，但要注意避免强引用循环（一个对象存储着一个闭包属性，同时这个属性又引用了这个对象）。

###Trailing closures
这个特性是 Swift 为了更好的可读性增加的一个语法甜头，当方法的最后一个参数是闭包时，为避免闭包内容冗长而导致可读性下降，可以将代码段写在参数括号外，函数会将其自动最为最后一个参数调用：

{% codeblock lang:swift %}
UIView.animateWithDuration(0.5）{
    vw.alpha = 0
}	//如果函数只有闭包一个参数，可以省略掉()
{% endcodeblock %}


至此 Hacking with Swift 教程的语言基础部分完成了，接下来开始着手 Project 部分，边敲项目边学习。

拓展阅读：[The new feature of Swift 2.0 by example](https://www.hackingwithswift.com/new-features-swift-2)

*本文根据自己的理解写下的学习笔记，由于英语和技术水平有限，一定会有不少错误和纰漏，请以原文和官方文档为准，如果能在评论中指出错误则感激不尽。*
