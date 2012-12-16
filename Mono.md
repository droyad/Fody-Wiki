# Mono and MonoDevelop

## Enable XBuild 

To use Fody on Mono you will need to enable XBuild in MonoDevelop

### On Windows

`Tools > Options > Preferences > Build > Compile projects using MSBuild / XBuild`

### On OSX

`MonoDevelop > Preferences > Preferences > Build > Compile projects using MSBuild / XBuild`

### Screenshot
![XBuildWindows.png](https://raw.github.com/wiki/SimonCropp/Fody/XBuildWindows.png)

## Add to Solution and Projects

Since there is no VS addin model in MonoDevelop you will need to do a little manual work to setup Fody in your solution. 

See [Setup](Setup)