Reproduces a bug in build comparison in GE.

First clone this repository to 2 different directory locations. These location should _not_ be siblings, because they would then share the same 'out' directory.

1. Run `./gradlew clean check` in checkout 1
2. Repeat `./gradlew clean check` in checkout 1
3. Run `./gradlew clean check` in checkout 2

The comparison between 1 & 2 will correctly report a difference in `gen-resources/resources.prop`.
The comparison between 1 & 3 will incorrectly report "File is only declared as an input in build A." for `resources.prop`. 

