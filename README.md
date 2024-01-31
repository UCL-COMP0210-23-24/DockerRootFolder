# DockerRootFolder

Root folder for those using Docker on COMP0210. Open VSCode from here and then re-open in container to work within the container. 

To avoid having to rebuild the image, and reinstall things like Catch2, you can work from within this folder and clone each week's exercises into a sub-folder, reusing the same image each week. 

## Installing Catch2 

You can clone the [Catch2 repository here](https://github.com/catchorg/Catch2). To install you should complete the following steps (using your VSCode terminal while inside your container):

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


