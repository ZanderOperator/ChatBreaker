# ChatBreaker

[![sampctl](https://img.shields.io/badge/sampctl-ChatBreaker-2f2f2f.svg?style=for-the-badge)](https://github.com/ZanderOperator/ChatBreaker)

<!--
Short description of your library, why it's useful, some examples, pictures or
videos. Link to your forum release thread too.

Remember: You can use "forumfmt" to convert this readme to forum BBCode!

What the sections below should be used for:

`## Installation`: Leave this section un-edited unless you have some specific
additional installation procedure.

`## Testing`: Whether your library is tested with a simple `main()` and `print`,
unit-tested, or demonstrated via prompting the player to connect, you should
include some basic information for users to try out your code in some way.

And finally, maintaining your version number`:

* Follow [Semantic Versioning](https://semver.org/)
* When you release a new version, update `VERSION` and `git tag` it
* Versioning is important for sampctl to use the version control features

Happy Pawning!
-->

## Installation

Simply install to your project:

```bash
sampctl package install ZanderOperator/ChatBreaker
```

Include in your code and begin using the library:

```pawn
#include <ChatBreaker>
```

## Usage

<!--
Write your code documentation or examples here. If your library is documented in
the source code, direct users there. If not, list your API and describe it well
in this section. If your library is passive and has no API, simply omit this
section.
-->
This library is fairly simple. It ALS hooks a function that basically filters through long strings, look for ' '(space) chars, and break the message in two line if string length is larger than ```LINE_BREAKING_LENGTH```. 

It implements this feature in two PAWN natives:
```
SendClientMessage(playerid, color, const string[]);
SendClientMessageToAll(color, const string[]);
```

Also, it supports passing embedded colors. For example: your string has 102 chars, embedded color starts at 60th char, and last space is on 86th char. Function will break/split that string on 86th character, add 3 dots on the place of space in the first line, and "pass" the embedded color at the start of the rest of the string with 3 dots on beginning of the string. 

If there is no space in between 20 chars before the ```LINE_BREAK_LENGTH``` is reached, chat line simply won't break/split, and will be sent in its original, unbroken state.

## Testing

<!--
Depending on whether your package is tested via in-game "demo tests" or
y_testing unit-tests, you should indicate to readers what to expect below here.
-->

To test, simply run the package:

```bash
sampctl package run
```
Example short ```SendClientMessage``` and long ```SendClientMessageToAll``` will be executed on ```OnPlayerConnect``` callback.
