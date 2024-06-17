While there are unique use cases, these standards should be viewed as the default for the club. 

# C++
1. Default to `C++20` 
2. Use clang-format and the `.clang-format` file in this folder to format code
3. Follow the Google C++ style guide found [here](https://google.github.io/styleguide/cppguide.html) 
	* **except** for:
		* Their stance on exceptions. We permit exceptions
		* Their formatting guidelines where they conflict with our formatting standards found in the `.clang-format` file
	* Call Outs for extra robust C++ code:
		* [Integer Types](https://google.github.io/styleguide/cppguide.html#Integer_Types)
		* [Use of Const](https://google.github.io/styleguide/cppguide.html#Use_of_const)
		* [Ownership And Smart Ptrs](https://google.github.io/styleguide/cppguide.html#Ownership_and_Smart_Pointers)
		* [Local Variables](https://google.github.io/styleguide/cppguide.html#Local_Variables)
4.  For static analysis, prefer `clang-tidy`. There is an example `.clang-tidy` file in this folder. It basically is a more opinionated compile warning machine. If you are new to C++, I suggest using it as it can save you from some of the more pointy foot guns.

# Python
1. Target Python 3.10
	1. The rationale here is that this is the version shipped by the version of Ubuntu we target (Jellyfish). It is also older than 3.12 which [removes support for distutills](https://peps.python.org/pep-0632/) and may break the build system of older ROS packages
2. Follow [PEP 8](https://peps.python.org/pep-0008/) for formatting. Use `black` for this 
3. Prefer type hints so readers of your code don't need to read the entire module to know type what a local variable is. [PEP 484](https://peps.python.org/pep-0484/) [typing module docs](https://docs.python.org/3/library/typing.html)
4. For static analysis, try [`pylint`](https://pypi.org/project/pylint/)