# RLB Java Style Guide
_If a RLB member wants to add or modify style restrictions, make a pull request with an explanation and reasoning._

Welcome! This documentation aims to provide guidance to produce both efficient and maintainable Java code.

## Chapters
1. Indentation guidelines
2. Brackets and spacing guidelines
3. Object oriented programming guidelines

___

## C1: Indentation Guidelines
Code should use 3 spaces per tab indentation. The reasoning for this is quite simple;
4 tabs pushes code more to the right of the screen, but 2 tabs makes statements stand out less and appear more cluttered.

The solution to this is 3 spaces per tab.

While this might seem quite unusual and you might think this would lead to inconsistencies,
Android Studio automatically corrects areas of code with different spaces per tab.

___

## C2: Brackets and spacing guidelines
### Statements and loops
All if statements will use spacing as in this example:
```
if (i > 20) {
```
There should be a space around `if ()` and one space before the opening bracket `() {`

In Java _or any C family language_, you could do
```
if (sysVoltage < 10) {
   exceptionTime += loopTime / 1000;
}
```
or if you wanted to save space, you can do:
```
if (sysVoltage < 10)
   exceptionTime += loopTime / 1000;
```
The bracket-less form only works if the statement has one line of code.

Either of these is valid. The issue is that using bracket-less form creates inconsistency with the rest of the codebase.
Because of this, only use the bracket-less form when there are **2 or more** statements next to each other.

For example:
```
for (final var motor : brakeMotors)
   motor.setZeroPowerBehavior(DcMotorEx.ZeroPowerBehavior.BRAKE);
for (final var motor : encoderMotors)
   motor.setMode(DcMotorEx.RunMode.RUN_USING_ENCODER);
for (final var motor : reverseMotors)
   motor.setDirection(DcMotorEx.Direction.REVERSE);
```
saves a significant amount of space compared to
```
for (final var motor : brakeMotors) {
   motor.setZeroPowerBehavior(DcMotorEx.ZeroPowerBehavior.BRAKE);
}
for (final var motor : encoderMotors) {
   motor.setMode(DcMotorEx.RunMode.RUN_USING_ENCODER);
}
for (final var motor : reverseMotors) {
   motor.setDirection(DcMotorEx.Direction.REVERSE);
}
```
### Usage of spacing in single line bracketed constructs
All items/contents within `{}` will be spaced out from the brackets.
For example:
```
final DcMotorEx[] encoderMotors = { frontLeft, frontRight, backLeft, backRight, indexer };
```
As you can see, after `{` there is a space before the rest of the contents, and a space before the closing bracket `}`.

The space cost is very little, and it looks decently cleaner compared to
```
final DcMotorEx[] encoderMotors = {frontLeft, frontRight, backLeft, backRight, indexer};
```
___

## C3: Object oriented programming guidelines
WIP :)
___
