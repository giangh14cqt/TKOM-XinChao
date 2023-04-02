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
`int, float, bool`

#### Operation:
`+, -, *, /, <, >, <=, >=, ==, !=, +=, -=`\
`&&, ||, !`

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