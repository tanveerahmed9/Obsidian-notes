#Go


// **runtime** package 

Package to analyse the runtime informartion of the GO code, Example below



Defer Keyword:-

Defers the execution of the function until the surrounding function returns (generally used in File I/O ops)

Deferred functions are executed LIFO order.

For examples refer VS Code


// Package main

import {
 "fmt"
}

func d1(){

}
///////////////
//////////////

// panic and recover

panic - > built in function which can be used by the developer in case he/she wants to end the program if an unwanted condition is met.

Recover -> another built in function which can be used in case you want to recover from a panic situation , for example if the disk usage is higher than 90% we want to panic and also call the cleanup which cleans up based on pre-defined rules.


Exploring runtime package:-

// fetch OS and runtime info using this package

func runtimeTest() {

fmt.Print("on a ", runtime.GOARCH, "machine")

fmt.Println("number of CPU's:", runtime.NumCPU())

fmt.Println("Number of GoRoutines", runtime.NumGoroutine())

}



// Node Tree 

   go tool compile -W main.go 
   
   to fetch before Data
   
   go tool compile -W main.go | grep before
   
   Output :-
   
before walk os.(*File).close
before walk main
before walk printStat
before walk type..eq.[2]interface {}
before walk loopMemoryDemo
before walk mapDemo
before walk logD1
before walk logD2
before walk logD3
before walk panica
before walk cleanupRecover
before walk runtimeTest
before walk type..eq.[3]interface {}
before walk goTreeTest
before walk logD2.func1
before walk logD3.func1
   
   
   to fetch after data
   
   go tool compile -W main.go | grep after
   
  after walk os.(*File).close
after walk main
after walk printStat
after walk type..eq.[2]interface {}
after walk loopMemoryDemo
after walk mapDemo
after walk logD1
after walk logD2
after walk logD3
after walk panica
after walk cleanupRecover
after walk runtimeTest
after walk type..eq.[3]interface {}
after walk goTreeTest
after walk logD2.func1
after walk logD3.func1




   
   


