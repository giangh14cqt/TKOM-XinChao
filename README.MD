# TKOM Project - Warsaw University of Technology

Project name: `XinChao` \
Author: Truong Giang Do \
Mentor: Wysota Witold

## Description

The goal of the project is to write a language interpreter with a similar to C/C++ but it has a simpler syntax.

The interpreter was written entirely in C++; the libraries used are only standard libraries (C++17 - including std::variant ).

```
int n = 1
for n < 5 {
    print(n)
    n *= 2
}
```

## Characteristics of the language

Support data types:\
`int, float, bool`

Operation:\
`+, -, *, /, <, >, <=, >=, ==, !=, +=, -=`\
`&&, ||, !`

Keywords and other symbols:\
Block:
```
{

}
```
Loop:
```
for <initialization statement>; <condition expression>; <post statement> {
    <action>
}
```
Condition:
```
if () {

}
```
Condition with else:
```
if () {

} else {

}
```