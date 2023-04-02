# TKOM Project - Warsaw University of Technology

Project name: `XinChao` \
Author: Truong Giang Do \
Mentor: Wysota Witold

## Description

The goal of the project is to write a language interpreter with a similar to C/C++ but it has a simpler syntax.

The interpreter was written entirely in C++; the libraries used are only standard libraries (C++17 - including std::variant ).

```
for int i=1; i < 5; i+=1 {
    print(i)
    i *= 2
}
```

## Characteristics of the language

#### Support data types:
`int, float, bool, string, vector`

#### Operation:
`+, -, *, /, <, >, <=, >=, ==, !=, +=, -=`\
`&&, ||, !`

#### Variable
Declare variable:
```
<data type> <variable's name>
int n
```
Declare variable with value:
```
<data type> <variable's name> = <value>
int n = 5
```
Declare constain variable:
```
const <data type> <variable's name> = <value>
const int n = 10
```
#### Statement
```
{
    <block statement>
}
```

```
<basic statement>
int n = 5
```

```
<Function parameters in parentheses>
(n < 5)
```

#### Loop:
```
for <initialization statement>; <condition expression>; <post statement> {
    <action>
}
for <variable> in <vector> {
    <action>
}
```
#### Condition:
```
if <condition expression> {

}
```
#### Condition with else:
```
if <condition expression> {

} else {

}
```
#### Object
`class` - keyword to define a class \
`new` - keyword to create new object \
`this` - keyword to denote class attributes

#### Function
Declare a function: 
```
<data type to return> <function's name> (<data type> <parametr 1>, <data type> <parametr 2>, ...) {
    return <value to return>
}

int calculate(int a, int b) {
    return a + b
}
```

#### Built-in function
`print()` - print text, variables\
`range(<start>, <stop>, <step>)` -  return a vector of integers from <start> to <stop> with the given <step>\
`typeof()` - return type of a variable

#### Comment
`//` - text after this symbol is consider as comment

## Examples of language constructions

#### Declare variables and mathematical, logical operations:
```
int x = 1 + 2 - 3 + 4 * (6 / 3)
x += 1
float y = 10.0 / 3
bool compare = x > y
bool compare2 = compare && ( x > 10 )
string str = "XinChao"
```
#### Operation with vector:
```
vector<int> vec;
vec.add(1)  // Append an element with value 1 to the vector
vec.add(2)

print(vec.get(0))   // it should print: 1
print(vec.get(1))   // it should print: 2

vec.pop(1)  // Delete the element with index 1 from the vector
vec.pop(0)
```
#### Loop and condition statement
```
vector<int> list = range(1, 10, 2)
print("Odd numbers from 1 to 10 is: \n")
for i in list {
    print(i, " ")
}
print("Numbers from 1 to 10 is: \n")
for int i = 1; i <= 10; i+=1 {
    print(i, " ")
}
```

#### Define class and function
```
class Car {
    Car(string name) {
        this.name = name
    }
    string getName() {
        return this.name
    }
}

void main() {
    Car car = new Car("BMW")
    print(car.getName(), "\n")
    if car.getName == "Merc" {
        print("Merc car)
    } else {
        print("Not a Merc car")
    }
}
```

## Incorrect constructs and exception messages

#### Lexical level
```
int a = "asbc"
Undefined expression at line 1 position 9
```
#### Syntactical level
```
if a > b 
    print(a)
Undefined expression at line 2 position 5: opening curly bracket not found
```
#### Semantic level
```
int a = 1
a += "2"
Unsupport operation in line 2 position 6
```
```
print(4/0)
Division by 0 at line 1 position 9
```

## Grammar

#### Syntax

- program               = function-definition | class-definition;
- function-definition   = type, identifier, "(", [parameters-list], ")", block;
- class-definition      = "class", identifier, class-body;
- parameters-list       = type, identifier, {",", type, identifier};
- class-body            = "{", {constructor}, {function-definition},"}";
- constructor           = identifier, block;
- identifier            = letter, {letter | digit};
- block                 = "{", {statement}, "}";
- statement             = object-access, [assignment]
                        | if-statement
                        | for-statement;
- object-access         = title, {".", title};
- title                 = identifier, ["(", arguments-list, ")"];
- if-statement          = "if", expression, block, ["else", block];
- for-statement         = "for", identifier, "in", object-access, block
                        | "for", statement, ",", expression, ",", statement, block;
- assignment            = ("=" | "+=" | "-="), expression;
- expression            = or-expression;
- or-expression         = and-expression, {'||', and-expression};
- and-expression        = relative-expression, {'&&', relative-expression};
- relative-expression   = arithmetic-expression, {relative-operator, arithmetic-expression};
- arithmetic-expression = multiplicative-expression, {("+" | "-"), multiplicative-expression};
- multiplicative-expression   = factor, {("*" | "/"), factor};
- factor                = [negation], (literal | object-access | object-creation | "(", expression, ")");
- object-creation       = new-keyword, identifier, "(", [arguments-list], ")";
- identifier            = letter, {letter | digit};
- literal               = integer
                        | float
                        | bool
                        | string

#### Lexical

- type                  = "int" | "float" | "bool" | "string"
- negation              = "!"
- new-keyword           = "new"
- relative-operator     = "==" | "<" | ">" | ">=" | "<=" | "!="
- nonZeroDigit          = "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"
- digit                 = "0" | nonZeroDigit
- letter                = "A" | "B" | "C" | ... | "Z" | "a" | "b" | "c" | ... | "z" | "_"
- special-symbol        = " " | "\" | "!" | "@" | ...
- integer               = nonZeroDigit, {digit}
- float                 = integer, ".", digit, {digit}
- bool                  = "true" | "false"
- char                  = {letter} | {digit} | {special-symbol}
- string                = '"', {char}, '"'