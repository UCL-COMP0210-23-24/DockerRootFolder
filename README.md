# DockerRootFolder

Root folder for those using Docker on COMP0210. 

This folder in VSCode either by navigating to it in the terminal and typing `code .` or by clicking "File -> Open Folder" in the VSCode menu and selecting this folder. 

Re-open the folder in the container. In the bottom right hand corner a dialogue box should automatically appear suggesting this, but if not you can click the blue `><` symbol in the bottom left and select "Reopen in Container". The first time this happens, it will have to build, so it might take a while. On subsequent re-openings however it should be quicker. 

To avoid having to rebuild the image, and reinstall things like Catch2, you can work from within this folder and clone each week's exercises into a sub-folder, reusing the same image each week. 

## Installing Catch2 Inside Your Container

Once you have reopened in your container, you can clone the [Catch2 repository here](https://github.com/catchorg/Catch2). To install you should complete the following steps:

- Clone the repository. 
- Move into the Catch2 folder in your terminal.
- Use the following commands to build Catch2:

    ```
    cmake -B build -DBUILD_TESTING=OFF
    cmake --build build
    ```

If you have permissions and want to install system wide you can then run

```
cmake --install build/
```

Otherwise run 

```
cmake --install build/ --prefix install_path
```

where you replace `install_path` a path to a folder of your choice.

In your top level CMakeLists.txt you will see the following line, which should work for a global install:

```
find_package(Catch2 3 REQUIRED)
```

or if you have chosen a local install, you should uncomment and complete the lines below it:

```
 if(NOT Catch2_FOUND)
 {
     # add local install path if required.
     find_package(Catch2 3 REQUIRED PATHS install_path)
 }
 endif()
```

replacing `install_path` with the path to your chosen install folder. This allows cmake to find your Catch2 installation, including the header files and the compiled library.


