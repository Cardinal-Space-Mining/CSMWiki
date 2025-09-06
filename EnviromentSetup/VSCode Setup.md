Suggested Extensions:
* `CMake` : twxs
* `CMake Tools` : Microsoft
* `C/C++ Extension Pack` : Microsoft
* `Makefile Tools` : Microsoft
* `Python` : Microsoft
* `Python Debugger` : Microsoft
* `Pylance` : Microsoft
* `Black Formatter` : Microsoft

## Setting Up C++ Compilation Database:

Ros2 uses a tool called `colcon` for its build process. We will hook into the internal CMake process to generate a compilation database and feed that back to VSCode to use for error squiggles and autocomplete

1. Make sure `colcon` generates a compilation database. That is done by adding the command line arg `--cmake-args=-DCMAKE_EXPORT_COMPILE_COMMANDS:BOOL=ON` to colcon
2. Locate the file `compile_commands.json` in your build directory, right click, and hit `Copy Relative Path`
3. Hit View -> Command Pallet
4. Type in `C/C++: Edit configurations (UI)` and hit enter
5. Scroll down, make sure C++ Standard is set to 20 (the standard the club uses for Ubuntu C++ code)
6. Under `C/C++: Edit configurations (UI) -> Advanced Options -> Compile Commands` write `${workspaceFolder}/relative_path_to_compile_commands_found_in_step_2`
	1. ![[Pasted image 20240616214309.png]]
# Setting Up Formatters
1. Open your VSCode settings, by going `Code -> Preferences -> Settings`.
2. Search for `format on save` and then select `whole file` from the drop down menu:
	1. ![[uzdlux4cnlf3t6oj4tse.png]]
3. Search for `Formatting` and configure the formatter to use clangFormat
	1. ![[Pasted image 20240616230742.png]]
4. Search for `Clang_format_style`, set it to file
	1. ![[Pasted image 20240616230910.png]]
	2. This way it uses the `.clang-format` file found at the top level directory
5. Now when you save a python or C++ file, VSCode will automatically format the file
