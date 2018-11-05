# esp-examples
The mandatory ESP-IDF (ESP32) examples repository

# To import in eclipse
## Project Properties
The new project will appear under Project Explorer. Right-click the project and choose Properties from the context menu.

Click on the `C/C++ Build` properties page (top-level):

Uncheck `Use default build command` and enter this for the custom build command: 
`python ${IDF_PATH}/tools/windows/eclipse_make.py`

## Click on the “Environment” properties page under `C/C++ Build`:

Click “Add…” and enter name 
`BATCH_BUILD and value 1`
Click “Add…” again, and enter name 
`IDF_PATH C:/Users/user-name/Development/esp-idf`
Edit the `PATH` environment variable. Delete the existing value and replace it with 
`C:\msys32\usr\bin;C:\msys32\mingw32\bin;C:\msys32\opt\xtensa-esp32-elf\bin`
(If you installed msys32 to a different directory then you’ll need to change these paths to match).
Click on “C/C++ General” -> “Preprocessor Include Paths, Macros, etc.” property page:

## Click the “Providers” tab

### In the list of providers, click `CDT Cross GCC Built-in Compiler Settings`. 
Change `Command to get compiler specs` to `xtensa-esp32-elf-gcc ${FLAGS} -std=c++11 -E -P -v -dD "${INPUTS}`
### In the list of providers, click `CDT GCC Build Output Parser` 
change the `Compiler command pattern` to `xtensa-esp32-elf-(gcc|g\+\+|c\+\+|cc|cpp|clang)`

## Navigate to “C/C++ General” -> “Indexer” property page:
Check `Enable project specific settings` to enable the rest of the settings on this page.
Uncheck “Allow heuristic resolution of includes”. When this option is enabled Eclipse sometimes fails to find correct header directories.

## Navigate to “C/C++ Build” -> “Behavior” property page:

Check “Enable parallel build” to enable multiple build jobs in parallel.
Setting the number of jobs slightly higher than the “optimal” may give the absolute fastest builds under Windows, depending on the specific hardware being used.
