# RLB Java Style Guide
_If a RLB member wants to add or modify style restrictions, make a pull request with an explanation and reasoning._

Welcome! This documentation aims to provide guidance to produce both efficient and maintainable Java code.

## Chapters
1. Indentation guidelines
2. Brackets and spacing guidelines
3. Variable naming and declarations
4. Object oriented programming guidelines

___

## C1: Indentation Guidelines
Code should use 3 spaces per tab indentation. The reasoning for this is quite simple;
4 tabs pushes code more to the right of the screen, but 2 tabs makes statements stand out less and appear more cluttered.

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

```
if(sysVoltage < 10){ // <- Ugly!
   exceptionTime += loopTime / 1000;
}
```

.

In Java or any C family language, you could do
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
Because of this, only use the bracketless form when there are **3 or more** statements next to each other.

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

### Usage of spacing in equations and math operations
**There should always be spaces inbetween the operator and the number.**

For example, `if ((5 + 5) / 25.5 > 6) {` looks a lot better than `if((5+5)/25.5>6){`

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

## C3: Variable naming and declarations
### Immutability
When declaring a variable, you should start out with it as `final`.
As you shape the code over time and you develop the need to mutate it, you can drop the `final` in declaration.

The easiest variables to make `final` are:
* Hardware/Motor definitions  `final MotorEx frontLeft  = new MotorEx(hardwareMap, "frontLeft");`
* Class initializations       `final var Outtake  = new Outtake(outtake);`
* Objects in for-each loops   `for (final var module : modules)`

### Type usage
When making a simple variable that only holds a number or a string,
you should declare it with the appropriate type keyword.

While you could make
```
double driveX  = Range.clip(gamepad1.left_stick_x,  -motorMax, motorMax) * DRIVE_X_BIAS;
double driveY  = Range.clip(gamepad1.left_stick_y,  -motorMax, motorMax) * DRIVE_Y_BIAS;
double driveRx = Range.clip(gamepad1.right_stick_x, -motorMax, motorMax) * DRIVE_TURN_BIAS;
```
use the `var` keyword, you should always avoid `var` for primitive math and calculations
where keeping the data type explicit prevents bugs.

The `var` keyword should be saved for more complex objects, such as:
* Most class declarations `final var Debug = new Debug(telemetry);`
  _Note:_ `MotorEx` declarations cannot be `var`. You must instead use their respective type (MotorEx)
* `hardwareMap` objects
* Objects in forEach loops

When using `var`, keep in mind that you cannot use it on uninitialized variable declarations.

### Naming
All variables should use _camelCase_ for naming.
Do not use Hungarian notation (putting the variable type name's first letter as the first "word")

When deciding what to name a variable, you should think about:
* Compactness (should be no more than 3 words packed into the name)
* Understand-ability (Abbreviations are particularly bad, for example _bg_ vs _background_, _intakeC_ vs _intakeCurrent_)
* Clarity of measurement (naming `loopTime` `loopTimeMilliseconds` does make it more verbose, but makes it clearer later on when it is used.)

All variables should be easy the understand for someone unfamiliar with the program's code.

## C4: Object oriented programming guidelines
### Motor and Servo hardwareMap declarations
All `hardwareMap` declarations should happen in the _Main_ class to avoid repetition.
To hand off control of a motor to a class, pass it in through the class's init function.
```
final var Transfer = new Transfer(intaker, indexer); // Motors being passed into init function
```
Transfer class init function:
```
private final MotorEx intaker, indexer;

public Transfer(final MotorEx intaker, final MotorEx indexer)
{
   this.intaker = intaker;
   this.indexer = indexer;
}
```
WIP :)
___
