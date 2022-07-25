---
title: Custom errors

---
<!--Create a custom error-->
Go also allows for the creation of custom errors using the `Error()` function. 
To do this, the pre-declared error interface must be satisfied. 
Custom errors help us in tracing issues in the code faster.

Below is an elementary example of a custom error:

{{copy filename='code.go'}}
```go
package main

import (
	"fmt"
)

type theError struct {
}

func (m *theError) Error() string {
	return "fatal error!"
}

func startHere() (string, error) {
	return "", &theError{}
}

func main() {
	x, err := startHere()
	if err != nil {
		fmt.Println("Unexpected error:", err)
	} else {
		fmt.Println("The string:", x)
	}
}
```
{{ /copy }}

From the code above `theError()` implements `Error()` and thus satisfies error interface.  The `Error()` function returns a string.

Use the command below to run the application:

{{ execute }}
```
go run code.go
```
{{ /execute }}

Next, we’ll discuss the key takeaways.