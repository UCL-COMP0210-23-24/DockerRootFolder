# DockerRootFolder

Root folder for those using Docker on COMP0210. 

**IMPORTANT: You should clone this repository using the following command in order to also clone Catch2 as a submodule:**
```
git clone --recurse-submodules git@github.com:UCL-COMP0210-23-24/DockerRootFolder.git
```

This folder in VSCode either by navigating to it in the terminal and typing `code .` or by clicking "File -> Open Folder" in the VSCode menu and selecting this folder. 

Re-open the folder in the container. In the bottom right hand corner a dialogue box should automatically appear suggesting this, but if not you can click the blue `><` symbol in the bottom left and select "Reopen in Container". The first time this happens, it will have to build, so it might take a while. On subsequent re-openings however it should be quicker. 

To avoid having to rebuild the image, and reinstall things like Catch2, you can work from within this folder and clone each week's exercises into a sub-folder, reusing the same image each week. 

## Installing Catch2 Inside Your Container

Once you have reopened in your container, you can clone the [Catch2 repository here](https://github.com/catchorg/Catch2). To install you should complete the following steps:

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
