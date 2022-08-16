# Cascade
Created by [J.R. Williams (PixlPerfect01)](https://github.com/pixlperfect01)
## A Brief Overview
Cascade is a general purpose programming language with a focus on being as flexible as interpreted languages and as fast as compiled languages. It comes in a 32 bit and 64 bit form for desktops and laptops, and an 8 bit and 16 bit form for embedded devices.

Cascade 32/64 bit can be run on x86, ARM, and RISC-V processors. Cascade Embedded can only be run on ARM and RISC-V processors.
## Getting Started
To start off, you will need to [install]() the Cascade compiler on your machine. Once that is done, go into your favorite IDE / Editor and create a `main.cas` file. This is where you will be writing the majority of your code in basic projects.

In your `main.cas` file, type or paste the following code:
```cas
fn int main(string[] args){
	
}
```
What this snippet of code does in define a function (`fn`) with a return type of `int` called `main` that takes an array of strings called "args" `string[] args`. This is the entry point of your new Cascade program!  The parameters passed to this function will be the command line arguments **NOT INCLUDING THE PROGRAM NAME**.

However interesting that is, it does absolutely nothing useful. Let's print something to the terminal!
```cas
using io as *;
fn int main(string[] args){
	print.ln("Hello, World!");
}
```
This little program will print out the string "Hello, World!" to the terminal!

As you may have noticed by now, our `main` function should return an `int`, but there is no return statement anywhere! This is due to the fact that all primitive types (and even some custom ones!) have a property called "default". This is the value that gets returned from a function if no return statement is encountered! For `int`, this value is `0`.

Great! We got text onto the screen! But that's not a very interactive program, is it? Let's get some input from out user and say it back to them!
```cas
using io as *;

fn int main(string[] args){
	string userInput = read.ln("> ");
	print.ln(userInput());
}
```
What's new in this section is the `using` keyword, and the `read` object! What `using` does is include code from another file into the current one! The `read` object is used for getting text input from the user!

Next topics: loops, strings, and macros!
```cas
using math as m;
using io as *;

macro void err(string text){
	print.ln("Error parsing math equation!", Format.Colors.Red);
}

fn int main(string[] args){
	while(true){
		string userInput = read.ln("> ");
		if(userInput.isAny("exit", "quit", "break"){
			break;
		}
		try{
			double output = m.fromString(userInput);
			print.ln(output.toString());
		} catch (m.MathError.Parse as e) {  
			err("Error parsing math equation!");
			err(e.where);
		} catch(* as e) {
			err("Unexpected error occoured!");
			throw e;
		}
	}
}
```
