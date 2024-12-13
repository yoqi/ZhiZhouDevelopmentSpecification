# Flutter Development Guidelines

In the process of years of Flutter development, the following development guidelines have been summarized. Following these guidelines helps avoid most common mistakes. Additionally, using the same set of standards within a team ensures good readability of the code.

## Project Structure

Flutter code can be used to develop Android and iOS applications, and with Flutter 2.0, it also supports compiling for web, Windows, Linux, macOS, and other systems. Due to the randomness of Flutter plugins, try to minimize their use. Before using a plugin, check whether its source code is safe and efficient. If not, consider implementing it yourself.

Flutter Project Structure:

## Code Style

### Three Types of Identifiers

#### Upper Camel Case

For classes, enums, typedefs, and type parameters:

```
  class SliderMenu { ... }

  class HttpRequest { ... }

  typedef Predicate = bool Function<T>(T value);
```

Including classes used for metadata annotations:

```
  class Foo {
    const Foo([arg]);
  }

  @Foo(anArg)
  class A { ... }

  @Foo()
  class B { ... }
```

#### Use lowercase with underscores for libraries and source file names

Since Windows file systems are case-insensitive, in Flutter, Python, and other environments, source code file (library) names should be in lowercase with underscores.

```
  library peg_parser.source_scanner;

  import 'file_system.dart';
  import 'slider_menu.dart';
```

Avoid this style:

```
  library pegparser.SourceScanner;

  import 'file-system.dart';
  import 'SliderMenu.dart';
```

#### Use lowercase with underscores for import prefixes

```
  import 'dart:math' as math;
  import 'package:angular_components/angular_components'
      as angular_components;
  import 'package:js/js.dart' as js;
```

Avoid this style:

```
  import 'dart:math' as Math;
  import 'package:angular_components/angular_components'
      as angularComponents;
  import 'package:js/js.dart' as JS;
```

#### Use lowercase camel case for other identifiers

```
  var item;

  HttpRequest httpRequest;

  void align(bool clearItems) {
    // ...
  }
```

#### Prefer lowercase camel case for constant names

```
  const pi = 3.14;
  const defaultTimeout = 1000;
  final urlScheme = RegExp('^([a-z]+):');

  class Dice {
    static final numberGenerator = Random();
  }
```

Avoid this style:

```
  const PI = 3.14;
  const DefaultTimeout = 1000;
  final URL_SCHEME = RegExp('^([a-z]+):');

  class Dice {
    static final NUMBER_GENERATOR = Random();
  }
```

#### Avoid prefix letters

Since Dart can tell you the type, scope, mutability, and other attributes of a declaration, there is no need to encode these properties in the identifier name.

```
  defaultTimeout
```

Avoid this style:

```
  kDefaultTimeout
```

### Sorting

To keep your files tidy, there are guidelines on how imports should be ordered. Each "section" should be separated by a blank line.

#### Import Dart libraries before others

```
  import 'dart:async';
  import 'dart:html';

  import 'package:bar/bar.dart';
  import 'package:foo/foo.dart';
```

#### Import package libraries before relative imports

```
  import 'package:bar/bar.dart';
  import 'package:foo/foo.dart';

  import 'util.dart';
```

#### Third-party package imports should come before other packages

```
  import 'package:bar/bar.dart';
  import 'package:foo/foo.dart';

  import 'package:my_package/util.dart';
```

#### Export libraries after all imports in a separate section

```
  import 'src/error.dart';
  import 'src/foo_bar.dart';

  export 'src/error.dart';
```

Avoid this style:

```
  import 'src/error.dart';
  export 'src/error.dart';
  import 'src/foo_bar.dart';
```

### Always use braces for control flow structures

This avoids the "dangling else" problem.

```
  if (isWeekDay) {
    print('Bike to work!');
  } else {
    print('Go dancing or read a book!');
  }
```

#### Exception

If an if statement has no else clause and the entire if and then body fit on one line, you can omit the braces if you prefer.

```
  if (arg == null) return defaultValue;
```

If the body exceeds one line and needs to be split, use braces:

```
  if (overflowChars != other.overflowChars) {
    return overflowChars < other.overflowChars;
  }
```

Avoid this style:

```
  if (overflowChars != other.overflowChars)
    return overflowChars < other.overflowChars;
```

## Comments

### Format comments like sentences

Unless it is a case-sensitive identifier, the first word should be capitalized. End all comments with a period (or "!" or "?"). This applies to all types of comments: doc comments, inline comments, and TODOs, even for short fragments of sentences.

```
  greet(name) {
    // Assume we have a valid name.
    print('Hi, $name!');
  }
```

Avoid this style:

```
  greet(name) {
    /* Assume we have a valid name. */
    print('Hi, $name!');
  }
```

You can use block comments (/…/) to temporarily comment out a section of code, but all other comments should use `//`.

### Doc Comments

Use `///` for documenting members and types.

Use doc comments instead of regular comments so that `dartdoc` can find and generate documentation.

```
  /// The number of characters in this chunk when unsplit.
  int get length => ...
```

> Due to historical reasons, Dartmouth College supports two styles of doc comments: `///` ("C# style") and `/** ... */` ("JavaDoc style"). We prefer `///` because it is more compact. `/**` and `*/` introduce two empty lines in multi-line doc comments. In some cases, the `///` style is easier to read, especially when documenting lists with `-` bullet points.

### Consider writing doc comments for private APIs

Doc comments are not only for documenting public APIs used externally from a library. They also help understand private members that are called from other parts of the library.

#### Start doc comments with a brief one-sentence summary

Start the doc comment with a short, user-centric description, and end it with a period.

```
/// Deletes the file at [path] from the file system.
void delete(String path) {
  ...
}
```

Avoid this style:

```

```

#### Separate the first sentence of a doc comment into its own paragraph

Add a blank line after the first sentence to separate it into its own paragraph.

```
  /// Deletes the file at [path].
  ///
  /// Throws an [IOError] if the file could not be found. Throws a
  /// [PermissionError] if the file is present but could not be deleted.
  void delete(String path) {
    ...
  }
```

## Flutter_Go Usage Reference

### Library Imports

In Flutter Go, when importing libraries from the `lib` directory, always use the package name to avoid excessive `../../` paths.

```
package:flutter_go/
```

### String Usage

#### Concatenate adjacent string literals

If two string literals are adjacent (not values, but actual references to string literals), avoid using `+` to concatenate them. This is a good way to create long strings, but not for single-line strings.

```
raiseAlarm(
    'ERROR: Parts of the spaceship are on fire. Other '
    'parts are overrun by martians. Unclear which are which.');
```

Avoid this style:

```
raiseAlarm('ERROR: Parts of the spaceship are on fire. Other ' +
    'parts are overrun by martians. Unclear which are which.');
```

#### Prefer using template strings

```
'Hello, $name! You are ${year - birth} years old.';
```

#### Avoid using braces when not needed

```
  'Hi, $name!'
  "Wear your wildest $decade's outfit."
```

Avoid this style:

```
  'Hello, ' + name + '! You are ' + (year - birth).toString() + ' y...';
```

Avoid this style:

```
  'Hi, ${name}!'
  "Wear your wildest ${decade}'s outfit."
```

### Collections

#### Prefer using collection literals

If you want to create a fixed-size list or other custom collection types, always use a literal constructor.

```
  var points = [];
  var addresses = {};
  var lines = <Lines>[];
```

Avoid this style:

```
  var points = List();
  var addresses = Map();
```

#### Avoid using `.length` to check if a collection is empty

```
if (lunchBox.isEmpty) return 'so hungry...';
if (words.isNotEmpty) return words.join(' ');
```

Avoid this style:

```
  if (lunchBox.length == 0) return 'so hungry...';
  if (!words.isEmpty) return words.join(' ');
```

#### Consider using higher-order methods to transform sequences

If you have a collection and want to generate a new modified collection, use `.map()`, `.where()`, and other convenient methods on Iterable as they are shorter and more declarative.

```
  var aquaticNames = animals
      .where((animal) => animal.isAquatic)
      .map((animal) => animal.name);
```
Avoid using Iterable.forEach() with function literals

In Dart, the conventional method to iterate over a sequence is to use loops.

```dart
for (var person in people) {
  ...
}
```

The following style is not recommended:

```dart
people.forEach((person) {
  ...
});
```

#### Do not use List.from() unless you intend to change the result's type

Given an iterable, there are two obvious methods to generate a new list containing the same elements.

```dart
var copy1 = iterable.toList();
var copy2 = List.from(iterable);
```

The obvious difference is that the first one is shorter. The important difference is that the first one retains the original type parameter.

```dart
// Creates a List<int>:
var iterable = [1, 2, 3];

// Prints "List<int>":
print(iterable.toList().runtimeType);
```

```dart
// Creates a List<int>:
var iterable = [1, 2, 3];

// Prints "List<dynamic>":
print(List.from(iterable).runtimeType);
```

### Parameter Usage

#### Use '=' to separate named parameters from their default values

Due to historical reasons, Dart allows both ":" and "=" as separators for specifying default values for parameters. To be consistent with optional positional parameters, use "=".

```dart
void insert(Object item, {int at = 0}) { ... }
```

The following style is not recommended:

```dart
void insert(Object item, {int at: 0}) { ... }
```

#### Do not use explicit default values of null

If a parameter is optional and does not have a default value, the language implicitly uses null as the default value, so there is no need to write it.

```dart
void error([String message]) {
  stderr.write(message ?? '\n');
}
```

The following style is not recommended:

```dart
void error([String message = null]) {
  stderr.write(message ?? '\n');
}
```

### Variables

#### Do not explicitly initialize variables to null

In Dart, variables or fields that are not explicitly initialized are automatically initialized to null. Do not assign null unnecessarily.

```dart
  int _nextId;

  class LazyId {
    int _id;

    int get id {
      if (_nextId == null) _nextId = 0;
      if (_id == null) _id = _nextId++;
      return _id;
    }
  }
```

The following style is not recommended:

```dart
  int _nextId = null;

  class LazyId {
    int _id = null;

    int get id {
      if (_nextId == null) _nextId = 0;
      if (_id == null) _id = _nextId++;
      return _id;
    }
  }
```

#### Avoid storing things you can calculate

When designing classes, you usually want to expose multiple views to the same underlying state. Usually, you will see code that calculates all views in the constructor, then stores them:

The following style should be avoided:

```dart
  class Circle {
    num radius;
    num area;
    num circumference;

    Circle(num radius)
        : radius = radius,
          area = pi * radius * radius,
          circumference = pi * 2.0 * radius;
  }
```

Problems with the above code:

* Wastes memory
* Caching issues are invalid - how do you know when to recalculate the cache?

The recommended style is as follows:

```dart
  class Circle {
    num radius;

    Circle(this.radius);

    num get area => pi * radius * radius;
    num get circumference => pi * 2.0 * radius;
  }
```

### Class Members

#### Do not wrap unnecessary fields in getters and setters

The following style is not recommended:

```dart
  class Box {
    var _contents;
    get contents => _contents;
    set contents(value) {
      _contents = value;
    }
  }
```

#### Prefer using final fields to create read-only properties

Especially for `StatelessWidget`

#### Do not use `this` when it's not needed

The following style is not recommended:

```dart
  class Box {
    var value;

    void clear() {
      this.update(null);
    }

    void update(value) {
      this.value = value;
    }
  }
```

The recommended style is as follows:

```dart
  class Box {
    var value;

    void clear() {
      update(null);
    }

    void update(value) {
      this.value = value;
    }
  }
```

### Constructors

#### Prefer using the initializer form

The following style is not recommended:

```dart
  class Point {
    num x, y;
    Point(num x, num y) {
      this.x = x;
      this.y = y;
    }
  }
```

The recommended style is as follows:

```dart
class Point {
  num x, y;
  Point(this.x, this.y);
}
```

#### Do not use `new`

Dart 2 makes the `new` keyword optional

The recommended style is as follows:

```dart
  Widget build(BuildContext context) {
    return Row(
      children: [
        RaisedButton(
          child: Text('Increment'),
        ),
        Text('Click!'),
      ],
    );
  }
```

The following style is not recommended:

```dart
  Widget build(BuildContext context) {
    return new Row(
      children: [
        new RaisedButton(
          child: new Text('Increment'),
        ),
        new Text('Click!'),
      ],
    );
  }
```

### Asynchronous

#### Prefer using async/await over raw futures

The async/await syntax improves readability, allowing you to use all Dart control flow structures in asynchronous code.

```dart
  Future<int> countActivePlayers(String teamName) async {
    try {
      var team = await downloadTeam(teamName);
      if (team == null) return 0;

      var players = await team.roster;
      return players.where((player) => player.isActive).length;
    } catch (e) {
      log.error(e);
      return 0;
    }
  }
```

#### Do not use asynchronous operations when they are not necessary

If you can omit asynchronous operations without changing the behavior of the function, then do so.

```dart
  Future afterTwoThings(Future first, Future second) {
    return Future.wait([first, second]);
  }
```

The following style is not recommended:

```dart
  Future afterTwoThings(Future first, Future second) async {
    return Future.wait([first, second]);
  }
}



