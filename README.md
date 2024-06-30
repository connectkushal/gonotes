# gonotes

##### String Formater
- frequently used
  
|verbs| usage| example |
|--------|--------|--|
|%2d  | set width of the number, space as padding||
| %02d |`0` for padding ||
| %0*d | take width as user input. for space padding remove `0`| eg sprintf("%0*d", 3, 2) //002 |
| %.1f| print value with 1 precision | eg output `5.9` for input of `5.9238478`|
| %04.1f| set total width to 4 with 1 precision with 0 as padding| eg `02.1` for input of `2.123`|

- other verbs

```  
General:

%v  the value in a default format.
    when printing structs, the plus flag (%+v) adds field names
%#v a Go-syntax representation of the value
%T  a Go-syntax representation of the type of the value
%%  a literal percent sign; consumes no value

Boolean:

%t  the word true or false

Integer:

%b  base 2
%c  the character represented by the corresponding Unicode code point
%d  base 10
%o  base 8
%q  a single-quoted character literal safely escaped with Go syntax.
%x  base 16, with lower-case letters for a-f
%X  base 16, with upper-case letters for A-F
%U  Unicode format: U+1234; same as "U+%04X"

Floating-point and complex constituents:

%b  decimalless scientific notation with exponent a power of two,
    in the manner of strconv.FormatFloat with the 'b' format,
    e.g. -123456p-78
%e  scientific notation, e.g. -1234.456e+78
%E  scientific notation, e.g. -1234.456E+78
%f  decimal point but no exponent, e.g. 123.456
%g  whichever of %e or %f produces more compact output
%G  whichever of %E or %f produces more compact output

String and slice of bytes:

%s  the uninterpreted bytes of the string or slice
%q  a double-quoted string safely escaped with Go syntax
%x  base 16, lower-case, two characters per byte
%X  base 16, upper-case, two characters per byte

Pointer:

%p  base 16 notation, with leading 0x

Other flags:

+   always print a sign for numeric values;
    guarantee ASCII-only output for %q (%+q)
-   pad with spaces on the right rather than the left (left-justify the field)
#   alternate format: add leading 0 for octal (%#o), 0x for hex (%#x);
    0X for hex (%#X); suppress 0x for %p (%#p);
    print a raw (backquoted) string if possible for %q (%#q);
    write e.g. U+0078 'x' if the character is printable for %U (%#U).
' ' (space) leave a space for elided sign in numbers (% d);
    put spaces between bytes printing strings or slices in hex (% x, % X)
0   pad with leading zeros rather than spaces
```

Formatting Verbs

In addition to %s for string and %d for decimal, the 'fmt' package provides a wide range of format verbs for different types of data:

    %v: the value in a default format
    %+v: a representation of the value with field names (for structs)
    %#v: a Go-syntax representation of the value
    %T: a Go-syntax representation of the type of the value
    %t: the word true or false (for booleans)
    %b: the binary representation (for integers)
    %c : the character represented by the corresponding Unicode code point (for integers)
    %e, %E, %f, %F, %g, or %G: floating-point formatting (for floating-point and complex types)
```
package main

import "fmt"

type Person struct {
    Name string
    Age  int
}

func main() {
    alice := Person{"Alice", 30}
    fmt.Printf("%v\n", alice)  // {Alice 30}
    fmt.Printf("%+v\n", alice)  // {Name:Alice Age:30}
    fmt.Printf("%#v\n", alice)  // main.Person{Name:"Alice", Age:30}
    fmt.Printf("%T\n", alice)  // main.Person

    fmt.Printf("%t\n", true)  // true
    fmt.Printf("%b\n", 5)  // 101
    fmt.Printf("%c\n", 65)  // A

    fmt.Printf("%e\n", 123400000.0)  // 1.234000e+08
    fmt.Printf("%f\n", 123.456789)  // 123.456789
}
```
