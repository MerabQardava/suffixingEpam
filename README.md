# Suffixing App

The purpose of this exercise is to train you to design and package Java Applications, basing only on functional requirements.

To complete the exercise you have to design an application and package it to a runnable jar archive.
The name of the application is Suffixing App, its purpose is to rename files, adding a suffix to their names.
Once you have designed it, place the jar into [`src/main/resources`](src/main/resources) directory.
The name of the archive has to `suffixing.jar`. The archive must be runnable - it has to contain manifest with specified `Main-Class`.

## Suffixing App Specification
Here comes specification of the app:
- The application takes a single obligatory argument - the path to a config file.
- Config file format is `properties` (you may benefit from using `java.util.Properties` class) and contains three fields:
    - `mode` - renaming mode. Valid values (*case-insensitive*):
      - `copy` - keep the source file
      - `move` - remove the source file 
    - `suffix` - the suffix, that mut be added to the file name (*before* file extension).
    - `files` - a list of files for suffixing. File paths are separated with column`:`.
- The application must use a Logger (from `java.util.logging`) to log messages:
    - if mode from config is not recognized, log `Mode is not recognized: <mod_input_value>`, SEVERE level, then stop the execution.\
      Example: `Mode is not recognized: copi`
    - if suffix is not set, log `No suffix is configured`, SEVERE level, then stop the execution.
    - if files are not specified, log `No files are configured to be copied/moved`, WARNING level, then stop the execution.
    - if one of the specified files does not exist, log `No such file: <file-path>`, SEVERE level, but *do not stop* other files processing.
      Note, that file path in the message must contain *forward slashes* (`/`) to separate path parts, not backslashes.\
      Example: `No such file: src/test/resources/no-such-file.txt`
    - When copying a file, log `<source-file> -> <destination-file>`, INFO level.\
      Note, that file path in the message must contain *forward slashes* (`/`) to separate path parts, not backslashes.\
      Example: `src/test/resources/file.txt -> src/test/resources/file-suffix.txt`      
    - When moving a file, log `<source-file> => <destination-file>`, INFO level.\
      Note, that file path in the message must contain *forward slashes* (`/`) to separate path parts, not backslashes.\
      Example: `src/test/resources/file.txt => src/test/resources/file-suffix.txt`      
