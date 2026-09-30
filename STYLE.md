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
### How to Maintain Style
When copy-pasting portions of external Java code, the examples will very likely use 4 space tabs.
If you notice intermixing of these styles:
* Manually correct the issue if the issue is small.
* If the issue is large or across multiple files, go down to the bottom-right corner of the window.

Click `3 spaces`.

<img width="189" height="106" alt="Screenshot_2026-09-25_17-49-00" src="https://github.com/user-attachments/assets/d7e66cbe-f37b-4535-8730-6896e76e0482" />

___

Set `Tab size` and `Indent` to 3.

<img width="807" height="468" alt="Screenshot_2026-09-25_17-50-39" src="https://github.com/user-attachments/assets/8bf59597-cd8d-4fa9-b661-1a61eb5e6b7f" />

___

Finally, click `Ok` to apply the changes.

<img width="533" height="259" alt="Screenshot_2026-09-25_21-38-05" src="https://github.com/user-attachments/assets/2eb62a5b-8fad-4396-bcd0-0763720914ef" />

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
As you can see, after `{` there is a space before the rest of the contents.

All single 

___

## C3: Object oriented programming guidelines
WIP :)
___
