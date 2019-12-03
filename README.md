# Go
Group Members: Cristiano Firmani, Jayson Marshall, Rachel Ross, Justin Saborouh

[Essay Link](https://docs.google.com/document/d/1G_eh0lOtl0DZ1JZEYKoSsh-RG4AyFVAIgwK4pPHzDqE/edit?usp=sharing)
[Presentation Link](https://docs.google.com/presentation/d/1asJg6P7sjdwdhOy6yYZZmYkHltVAzXLwFNaaNEIaDFM/edit?usp=sharing)

## Why We Chose Go
Google’s programming language Go (also known as Golang) has become increasingly popular since its release. Go is currently the fourth most common programming language pushed onto Github and is the fastest growing. In the second quarter of 2018, Go had an overall growth of 7%, 1.5% from the previous quarter. Software developers are using Go to implement programming tasks that would have previously been written in other high-level languages such as Python, C, C++, or C# due to Go’s speed, simplicity, and reliability. More specifically Go offers benefits including cross-platform capability, native concurrency, depth of packages, and code that compiles to single binary (easy deployment). Google’s Go programming language has exponentially grown in popularity as it is being viewed as a superior statically-typed, scripting language. However, due to its immaturity, it is unclear as to whether it will prevail within the industry.

## History
At Google in 2007, programmers shared a common dislike of C++ for a wide range of reasons. Googlers wanted to design a new language that kept the capabilities of C++ in tact, but vastly increased programming productivity. These programmers wanted the new language to be statically-typed for high run-time efficiency, have high readability/useability, and have high performance networking as well as multiprocessing. In 2009, Go was formally announced and the first version was officially released in March of 2012. Naturally, Go is widely used at Google and has gained popularity from many other organizations throughout its existence. Go is now on its 14th version (1.13.1) and has been constantly improved throughout the years. Most recently, Google has looked to add generics and error handling capability which may appear in newer versions.

## When should it be used
The simplicity of Go allows it to excel when tasked with developing applications that are commercially viable. Among the developer community, the statement can be made that Go is the most suitable for producing utility type programs and server side applications. Examples of these backend applications include command line apps, databases, and network servers. In some cases, Go can be used for developing infrastructure and embedded systems software. Since it is considered to be user-friendly but still capable of creating complex, large-scale software, it is a viable choice for large programming teams with developers of varying skill levels, as well as those that deal with legacy code. With its growing popularity, more companies throughout the world are deciding to adopt Go as one of the programming languages used for their projects and services.

## Where is it used
The simplicity of Go allows it to excel when tasked with developing applications that are commercially viable. Among the developer community, the statement can be made that Go is the most suitable for producing utility type programs and server side applications. Examples of these backend applications include command line apps, databases, and network servers. In some cases, Go can be used for developing infrastructure and embedded systems software. Since it is considered to be user-friendly but still capable of creating complex, large-scale software, it is a viable choice for large programming teams with developers of varying skill levels, as well as those that deal with legacy code. With its growing popularity, more companies throughout the world are deciding to adopt Go as one of the programming languages used for their projects and services.

## Why is go suited for these tasks
Go should be chosen when looking for great efficiency in completing tasks concurrently, all the while maintaining robust, straightforward code. This need for efficiency strives from a shift in the hardware industry with more and more cores being added to processors. Most modern programming languages like Java and Python, were built in the 90s in a single threaded environment. Go, however, was released in 2009 when multi-core processors were readily available, meaning they kept concurrency in mind. Go has goroutines instead of threads, which only consume 2KB memory from the heap opposed to threads in other languages which take up 1MB. Go also implements the following: growable segmented stacks (only using more memory when needed); faster startup time; built-in primitives to communicate safely between themselves; no 1:1 mapping (allows a single goroutine to run on multiple threads). Go is even efficient on the compiling side of things, compiling directly onto the processor without a VM, removing one step and increasing performance. Finally, Go is simply built, going as far as removing certain features in order to maintain simplicity and robustness. Go does not have classes, inheritance, generics, or exceptions, in hopes to create easier to read code and cause less problems later on.

## Interesting features
The Golang is influenced by C/C++ and holds features that were designed to combat the common criticisms of the C language. It is designed to be dynamically typed, so declarations can be as straightforward as x := 0 instead of int x= 0. It also supports remote packaging management, similar to Java, where programmers can simply request packages with go get. A particularly interesting mechanic of Go is its built-in concurrency handling, where it is able to use light weight processes, called goroutines, for smooth threading. Additionally, it contains an interface system that replaces virtual inheritance with a convenient structure of global type embedment. Go also has a unique select statement, which functions similarly to a switch statement except that the case is chosen upon which case occurs first, which adds to the convenient threading design that Go revolves itself upon.

## Works Cited
https://hub.packtpub.com/why-golan-is-the-fastest-growing-language-on-github/
https://en.wikipedia.org/wiki/Go_(programming_language)#Applications
https://www.upwork.com/hiring/development/golang-programming-language/
https://medium.com/@kevalpatel2106/why-should-you-learn-go-f607681fad65
https://gobyexample.com/channels
https://medium.com/qash/golang-the-next-language-to-learn-for-developers-2c7c32b8a095
https://www.golang-book.com/books/intro/10

## Standard features not included in Go
* Classes
* Inheritance
* Constructors
* Annotations
* Generics
* Exceptions

## Benefits of goroutines
* 2KB of memory used per goroutine
* Implement growable segmented stacks
* Faster start times than threads
* Built-in primitives to communicate safely between themselves
* Allow you to avoid having to resort to mutex locking when sharing data structures
* No 1:1 mapping from goroutines to OS threads

## Why Go is so good for multithreading
### Channels
"Channels are the pipes that connect concurrent goroutines. You can send values into channels from one goroutine and receive those values into another goroutine."

### Goroutine example
```
package main

import (
    "fmt"
    "time"
)

func f(from string) {
    for i := 0; i < 3; i++ {
        fmt.Println(from, ":", i)
    }
}

func main() {

    f("direct")

    go f("goroutine")

    go func(msg string) {
        fmt.Println(msg)
    }("going")

    time.Sleep(time.Second)
    fmt.Println("done")
}
```
### Select example
```
package main

import (
    "fmt"
    "time"
)

func main() {

    c1 := make(chan string)
    c2 := make(chan string)

    go func() {
        time.Sleep(1 * time.Second)
        c1 <- "one"
    }()
    go func() {
        time.Sleep(2 * time.Second)
        c2 <- "two"
    }()

    for i := 0; i < 2; i++ {
        select {
        case msg1 := <-c1:
            fmt.Println("received", msg1)
        case msg2 := <-c2:
            fmt.Println("received", msg2)
        }
    }
}
```

## Channels Example
```
package main

import "fmt"

func main() {

    messages := make(chan string)

    go func() { messages <- "ping" }()

    msg := <-messages
    fmt.Println(msg)
}
```
[Online Go Compiler Link](https://play.golang.org/)
