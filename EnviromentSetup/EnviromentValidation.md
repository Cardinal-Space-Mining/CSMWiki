1. Clone the Git Setup Repo 
    1. `git clone https://github.com/Cardinal-Space-Mining/PurposefulyPrivateRepoForGitSetup.git`
2. Navigate into the Repo
    1. `cd ./PurposefulyPrivateRepoForGitSetup`
3. Open a VSCode instance
    1. `code .`
4. In a terminal inside VSCode, run these commmands to install packages needed by PurposefulyPrivateRepoForGitSetup:
    1. `sudo rosdep init` (If never used rosdep on that computer before)
    2. `rosdep update`
    3. `rosdep install -i --from-path ./src --rosdistro jazzy -y`
    4. `pip3 install -r ./requirements.txt`
5. Build the repo:
    1. `colcon build --executor parallel --cmake-args=-DCMAKE_EXPORT_COMPILE_COMMANDS:BOOL=ON`
        1. This will use all available CPU cores to build
        2. It will generate a `compile_commands.json` in the build directory.
6. Setup VSCode Intelesense
    1. Run the command `C\C++: Edit Configurations (UI)` in the VSCode Command Pallet (Ctrl + Shift + P)
    2. Scroll down to C++ Standard, set it to C++17
    3. In advanced settings, under compile commands, set the field to `${workspaceFolder}/build/compile_commands.json`
7. Test the compiled Binaries
    1. In a new VSCode terminal, run:
        1. `source /opt/ros/humble/setup.bash`
        2. `source ./install/setup.bash`
        3. `ros2 launch king_engine lance.launch.py`
    2. Most things will probably complain, as I doubt you have a 3D Lidar attached to your laptop, but assuming you get a bunch of output to stdout and no large errors running the above commands, your enviroment is setup correctly. Congrats!
