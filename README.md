# JavaScript Code Conventions


## File Format

Each file has this same basic format:

```js
/**
 * @fileoverview Why we are using this file.
 * @author Kumar Mrigendra
 */

"use strict";

//------------------------------------------------------------------------------
// Requirements
//------------------------------------------------------------------------------

// import modules
// require() statements

//------------------------------------------------------------------------------
// Helpers
//------------------------------------------------------------------------------

// private methods/data

//------------------------------------------------------------------------------
// Public Interface
//------------------------------------------------------------------------------

// exported objects/methods
module.exports = {

};
```

The `@author` field gives you credit for having created the file.

## Indentation

Each indentation level is made up of two spaces. Do not use tabs.

  if (true) {
  
    doSomething();
    
  }

## Primitive Literals String And Number Declaration

Strings should always use single quotes and should always appear on a single line. Never use a slash to create a new line in a string.

  const name = 'Nicholas';

Numbers should be written as decimal integers, e-notation integers, hexadecimal integers or floating-point decimals with at least one digit before and one digit after the decimal point. Never use octal literals.

  const count = 10;
  
  const price = 10.0;
  
  const price = 10.00;
  
  const num = 0xA2;
  
  const num = 1e23;

The special value `null` should be used only in the following situations:

1. To initialize a variable that may later be assign an object value.
1. To compare against an initialized variable that may or may not have an object value.
1. To pass into a function where an object is expected.
1. To return from a function where an object is expected.

Examples:

  const person = null;

  function getPerson() {
    if (condition) {
    
      return new Person('Nicholas');
      
    } else {
    
      return null;
      
    }
  }

  const person = getPerson();
  if (person !== null){
    doSomething();
  }

Never use the special value `undefined`. To see if a variable has been defined, use the `typeof` operator:

  if (typeof variable == "undefined") {
    // do something
  }

## Operator Spacing

Operators with two operands must be preceded and followed by a single space to make the expression clear. Operators include assignments and logical operators.

  const found = (values[i] === item);

  if (found && (count > 10)) {
    doSomething();
  }

  for (i = 0; i < count; i++) {
    process(i);
  }

## Parentheses Spacing

When parentheses are used, there should be no white space immediately after the opening paren or immediately before the closing paren.

  const found = (values[i] === item);

  if (found && (count > 10)) {
    doSomething();
  }

  for (i = 0; i < count; i++) {
    process(i);
  }

## Object Literals

Object literals should have the following format:

* The opening brace should be on the same line as the containing statement.
* Each property-value pair should be indented one level with the first property appearing on the next line after the opening brace.
* Each property-value pair should have an unquoted property name, followed by a colon (no space preceding it), followed by the value.
* If the value is a function, it should wrap under the property name and should have a blank line both before and after the function.
* Additional empty lines may be inserted to group related properties or otherwise improve readability.
* The closing brace should be on a separate line.

Examples:

  const object = {
    key1: value1,
    key2: value2,
    func: function() {
      // do something
    },
    key3: value3
  };

When an object literal is passed to a function, the opening brace should be on the same line as if the value is a variable. All other formatting rules from above still apply.

  doSomething({
    key1: value1,
    key2: value2
  });

## Comments

Make frequent use of comments to aid others in understanding your code. Use comments when:

* Code is difficult to understand.
* The code might be mistaken for an error.
* Browser-specific code is necessary but not obvious.
* Documentation generation is necessary for an object, method, or property (use appropriate documentation comments).

### Single-Line Comments

Single-line comments should be used to document one line of code or a group of related lines of code. A single-line comment may be used in three ways:

1. On a separate line, describing the code beneath it.
1. At the end of a line, describing the code before it.
1. On multiple lines, to comment out sections of code.

When on a separate line, a single-line comment should be at the same indentation level as the code it describes and be preceded by a single line. Never use multiple single-line comments on consecutive lines, use a multi-line comment instead.

  if (condition){
    // if you made it here, then all security checks passed
    allowed();
  }

For single-line comments at the end of a line, ensure there is at least one indentation level between the end of the code and the beginning of the comment:

  const result = something + somethingElse;    // somethingElse will never be null

The only acceptable time to have multiple single-line comments on successive lines is to comment out large sections of code. Multi-line comments should not be used for this purpose.

  // if (condition){
  //    doSomething();
  //    thenDoSomethingElse();
  // }

### Multi-Line Comments

Multi-line comments should be used to document code that requires more explanation. Each multi-line comment should have at least three lines:

1. The first line contains only the `/*` comment opening. No further text is allowed on this line.
1. The next line(s) have a `*` aligned with the `*` in the first line. Text is allowed on these lines.
1. The last line has the `*/` comment opening aligned with the preceding lines. No other text is allowed on this line.

The first line of multi-comments should be indented to the same level as the code it describes. Each subsequent line should have the same indentation plus one space (for proper alignment of the `*` characters). Each multi-line comment should be preceded by one empty line.

  if (condition){

    /*
     * if you made it here,
     * then all security checks passed
     */
    allowed();
  }

### Comment Annotations

Comments may be used to annotate pieces of code with additional information. These annotations take the form of a single word followed by a colon. The acceptable annotations are:

* `TODO` - indicates that the code is not yet complete. Information about the next steps should be included.
* `HACK` - indicates that the code is using a shortcut. Information about why the hack is being used should be included. This may also indicate that it would be nice to come up with a better way to solve the problem.
* `XXX` - indicates that the code is problematic and should be fixed as soon as possible.
* `FIXME` - indicates that the code is problematic and should be fixed soon. Less important than `XXX`.
* `REVIEW` - indicates that the code needs to be reviewed for potential changes.

These annotations may be used with either single-line or multi-line comments and should follow the same formatting rules as the general comment type. Examples:

  // TODO: I'd like to find a way to make this faster
  doSomething();

  /*
   * HACK: Have to do this for IE. I plan on revisiting in
   * the future when I have more time. This probably should
   * get replaced before v1.2.
   */
  if (document.all) {
    doSomething();
  }

  // REVIEW: Is there a better way to do this?
  if (document.all) {
    doSomething();
  }

  // Bad: Annotation spacing is incorrect
  // TODO : I'd like to find a way to make this faster
  doSomething();

  // Bad: Comment should be at the same indentation as code
    // REVIEW: Is there a better way to do this?
  if (document.all) {
    doSomething();
  }


## Variable Declarations

All variables should be declared before they are used. Variable declarations should take place at the beginning of a function using a `let/const` statement with one variable per line. All lines after the first should be indented one level so the variable names line up. Variables should be initialized when declared if applicable and the equals operator should be at a consistent indentation level. Initialized variables should come first followed by uninitialized variables.

  let count = 10;
  let name = 'Nicholas';
  let found = false;
  let empty;

Always declare variables. Implied globals should not be used.

## Function Declarations

Functions should be declared before they are used. When a function is not a method (not attached to an object) it should be defined using function declaration format (not function expression format nor using the `Function` constructor). There should be no space between the function name and the opening parentheses. There should be one space between the closing parentheses and the right brace. The right brace should be on the same line as the `function` keyword. There should be no space after the opening parentheses or before the closing parentheses. Named arguments should have a space after the comma but not before it. The function body should be indented one level.

  function doSomething(arg1, arg2) {
    return arg1 + arg2;
  }

Functions declared inside of other functions should be declared immediately after the `var` statement.

  function outer() {

  let count = 10;
  let name = 'Nicholas';
  let found = false;
  let empty;

    function inner() {
      // code
    }

    // code that uses inner()
  }

Anonymous functions may be used for assignment of object methods or as arguments to other functions. There should be no space between the `function` keyword and the opening parentheses.

  object.method = function() {
    // code
  };

Immediately-invoked functions should surround the entire function call with parentheses.

  const value = (function() {

    // function body

    return {
      message: "Hi"
    }
  }());

## Naming

Care should be taken to name variables and functions properly. Names should be limited to alphanumeric characters and, in some cases, the underscore character. Do not use the dollar sign (`$`) or back slash (`\`) characters in any names.

Variable names should be formatted in camel case with the first letter being lowercase and the first letter of each subsequent word being uppercase. The first word of a variable name should be a noun (not a verb) to avoid confusion with functions. Do not use underscore for variable names.

  const accountNumber = "8401-1";

Function names should also be formatted using camel case. The first word of a function name should be a verb (not a noun) to avoid confusion with variables. Do not use underscore for function names.

  function doSomething() {
    // code
  }

Constructor functions, those functions used with the `new` operator to create new objects, should be formatted in camel case but must begin with an uppercase letter. Constructor function names should begin with a non-verb because `new` is the action of creating an object instance.

  function MyObject() {
    // code
  }

Variables that act as constants (values that won't be changed) should be formatted using all uppercase letters with words separated by a single underscore.

  const TOTAL_COUNT = 10;

Object properties follow the same naming conventions as variables. Object methods follow the same naming conventions as functions. If a property or method is meant to be private, then it should be prefixed with an underscore character.

  const object = {
    _count: 10,

    _getCount: function () {
      return this._count;
    }
  };

## Strict Mode

Strict mode should be used in all modules, specified below the file overview comment and above everything else:

  "use strict";

  function doSomething() {
    // no "use strict" here

    // code
  }

## Assignments

When assigning a value to a variable, use parentheses around a right-side expression that contains a comparison.

  const flag = (i < count);

## Equality Operators

Use `===` and `!==` instead of `==` and `!=`. This avoids type coercion errors.

  const same = (a === b);

## Ternary Operator

The ternary operator should be used only for assigning values conditionally and never as a shortcut for an `if` statement.

  const value = condition ? value1 : value2;

## Statements

### Simple Statements

Each line should contain at most one statement. All simple statements should end with a semicolon (`;`).

  count++;
  a = b;

### return Statement

A return statement with a value should not use parentheses unless they make the return value more obvious in some way. Example:

  return;

  return collection.size();

  return (size > 0 ? size : defaultSize);

### Compound Statements

Compound statements are lists of statements enclosed inside of braces.

* The enclosed statements should be indented one more level than the compound statement.
* The opening brace should be at the end of the line that begins the compound statement; the closing brace should begin a line and be indented to the beginning of the compound statement.
* Braces are used around all statements, even single statements, when they are part of a control structure, such as a `if` or `for` statement. This makes it easier to add statements without accidentally introducing bugs due to forgetting to add braces.
* The statement beginning keyword, such as `if`, should be followed by one space and the opening brace should be preceded by a space.

### if Statement

The `if` class of statements should have the following form:

  if (condition) {
    statements
  }

  if (condition) {
    statements
  } else {
    statements
  }

  if (condition) {
    statements
  } else if (condition) {
    statements
  } else {
    statements
  }

It is never permissible to omit the braces in any part of an `if` statement.

  if (condition) {
    doSomething();
  }

### for Statement

The `for` class of statements should have the following form:

  for (initialization; condition; update) {
    statements
  }

  for (variable in object) {
    statements
  }

Variables should not be declared in the initialization section of a `for` statement.

  var i,
    len;

  for (i=0, len=10; i < len; i++) {
    // code
  }

When using a `for-in` statement, double-check whether or not you need to use `hasOwnProperty()` to filter out object members.

### while Statement

The `while` class of statements should have the following form:

  while (condition) {
    statements
  }

### do Statement

The `do` class of statements should have the following form:

  do {
    statements
  } while (condition);

Note the use of a semicolon as the final part of this statement. There should be a space before and after the `while` keyword.

### switch Statement

The `switch` class of statements should have the following form:

  switch (expression) {
    case expression:
      statements

    default:
      statements
  }

Each `case` is indented one level under the `switch`. Each `case` after the first, including `default`, should be preceded by a single empty line.

Each group of statements (except the default) should end with `break`, `return`, `throw`, or a comment indicating fall through.

  switch (value) {
    case 1:
      /* falls through */

    case 2:
      doSomething();
      break;

    case 3:
      return true;

    default:
      throw new Error("This shouldn't happen.);
  }

If a `switch` doesn't have a `default` case, then it should be indicated with a comment.

  switch (value) {
    case 1:
      /*falls through*/

    case 2:
      doSomething();
      break;

    case 3:
      return true;

    // no default
  }

### try Statement

The `try` class of statements should have the following form:

  try {
    statements
  } catch (variable) {
    statements
  }

  try {
    statements
  } catch (variable) {
    statements
  } finally {
    statements
  }

## White Space

Blank lines improve readability by setting off sections of code that are logically related.

Two blank lines should always be used in the following circumstances:

* Between sections of a source file
* Between class and interface definitions

One blank line should always be used in the following circumstances:

* Between methods
* Between the local variables in a method and its first statement
* Before a multi-line or single-line comment
* Between logical sections inside a method to improve readability

Blank spaces should be used in the following circumstances:

* A keyword followed by a parenthesis should be separated by a space.
* A blank space should appear after commas in argument lists.
* All binary operators except dot (`.`) should be separated from their operands by spaces. Blank spaces should never separate unary operators such as unary minus, increment (`++`), and decrement (`--`) from their operands.
* The expressions in a `for` statement should be separated by blank spaces. Blank spaces should only be used after semicolons, not before.

## Things to Avoid

* Never use the primitive wrapper types, such as `String`, to create new objects.
* Never use `eval()`.
* Never use the `with` statement. This statement isn't available in strict mode and likely won't be available in future ECMAScript editions.
