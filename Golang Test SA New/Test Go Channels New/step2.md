---
title: String-based errors

---
<!--Create string-based errors-->

String-based errors can either be formatted or plain. These errors are used when all you want to be returned is an error message. 
They can be created using either `errors.New()` or `fmt.Errorf()` methods.

- Plain errors: You use them when you want to return a fully predetermined message that won't contain more variables than when created. It is created using `errors.New()`.

- Formatted errors: You use them when you want to include a variable in the error message. It makes the error message more informative. It is created using `fmt.Errorf()`.

Below is an example using the two error types.

{{copy filename='code.go'}}
```go
package main

import (
	"errors"
	"fmt"
	"math"
)

func main() {
	x := math.Sqrt(-12)
	y := x / 0
	err1 := errors.New("math: square root of negative number")
	fmt.Println(err1)

	err2 := fmt.Errorf("math: operation on %f is impossible", y)
	fmt.Println(err2)
}
```
{{ /copy }}

From the code above, `errors.New()` method is used to create new errors and only takes the error message as its parameter. 
`fmt.Errorf()` method takes an error message and a variable as parameters.

Run the application using the command below:

{{ execute }}
```
go run code.go
```
{{ /execute }}

Next, we’ll discuss custom errors.