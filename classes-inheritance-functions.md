# Classes, Inheritance, Functions

## Functional Programing

- Distinction between pure & impure code
- Pure code has no side effects
- Pure functions can never mutate
- An impure function returns an unpredictable result

## High order functions

- A function that operates on another function
- can take a function in or output one

## Objects & Inheritance

- JavaScript objects use prototype-based inheritance
- Slightly different then strictly typed languages
- anything attached to a prototype can be used as its descendant
- using `class` & `extends` keywords inheritance is still in place
- Its just "syntactic Sugar"

## Errors

- Impotant for debugging
- JS has built in errors but you can make your own
- Writing good error messages is important
#### A great error message should have the following features

- timestamp so that a timeline of the error can be made
- message about the problem that occurred
- message about the cause of the problem
- consistent format (so that it can be parsed and searched)
- severity level (low, med high) or (0 - 10)

## Handling thrown errors

-  Errors can stop code from running
- Use a `try {} catch (error) {] to keep code running

## Error Cheat Sheet

|Type	|Reason|
|-----|:-----|
|Error	|generic error|
|ReferenceError	|an attempt was made to access a variable that is not defined|
|SyntaxError	|the javascript is not valid|
|TypeError	|a provided argument was no the allowable type|
SystemError	|a Node.js error that occurs when a system error has occurred|

## System Error Cheat Sheet

- `EACCESS` - an attempt to access a file without the right permissions
- `EADDRINUSE` - an attempt to start a server on a PORT that is already in use
- `ECONNREFUSED` - a connection was deliberately refused by the target machine
- `ECONNRESET` - a connection was forcibly closed by a peer
- `EEXIST` - a file exists and the attempted action required that it didn’t
- `EISDIR` - an action expected to act on a file but found a directory
- `EMFILE` - too many files were open for your operating system to handle
- `ENOENT` - an action expected a file, but did not find one
- `ENOTDIR` - an action expected a directory, but found something else
- `ENOTEMPTY` - an action expected an empty directory, but found one with data in it
- `EPERM` - an attempt to do something that you currently don’t have permissions to do
- `EPIPE` - an attempt to write data to a connection that had been closed
