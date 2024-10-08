# How To Modify Draw.io Pictures in the Architecture Whitepaper

## Preferred Mechanism

Due to differences in the way that different draw.io applications format the output, the preferred mechanism for modifying draw.io pictures included in the Architecture Whitepaper is to use Visual Studio. This will ensure that the differences you see when comparing versions of the draw.io file will only be those that have been made.

### Install Visual Studio

Follow the instructions from Microsoft on [How to Install Visual Studio](https://learn.microsoft.com/en-us/visualstudio/install/install-visual-studio).

### Install draw.io for VS Code Extension

Install the [draw.io for VSCode extension](https://marketplace.visualstudio.com/items?itemName=hediet.vscode-drawio).

## Alternative Mechanisms

You can also use the [online version of draw.io](https://draw.io) or download the [offline version of draw.io](https://github.com/jgraph/drawio-desktop/releases). 

**NOTE:** Using either of these mechanisms will result in multiple changes showing up in the git difference given that they format the output differently than that used in the VS Code extension.

# Creating a New Project Map

If you would like to create a new project map, please follow the instructions below:

1. Open the `architecture-whitepaper.drawio` file in Visual Studio Code (or one of the alternative mechanisms, if necessary).
2. Scroll to the right to find the `map-template` tab in the tabs list.
3. Right click the `map-template` tab and choose `Duplicate`. This will create a new tab named `Copy of map-template`.
4. Rename `Copy of map-template` by right clicking the tab and choosing `Rename...`. Name the file _project-name_-map.
5. Ensure that the Format pane is showing by clicking the draw.io `View` menu and ensuring that there is a check mark next to it.
6. Choose the capabilities that are supported (shift-click to select multiple items) and choose the `green` color under the Format Style tab.
