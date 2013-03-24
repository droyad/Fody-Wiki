# Sample Usage

### 1. Ensure nuget is installed 

[NuGet Visual Studio package](http://visualstudiogallery.msdn.microsoft.com/27077b70-9dad-4c64-adcf-c7cf6bc9970c) (required to consume addins via nuget)

### 2. Add the weaver nuget package

Install a Fody add-in using NuGet. See [Using the package manager console](http://docs.nuget.org/docs/start-here/using-the-package-manager-console) for more info. For this example we will use [Virtuosity](https://github.com/Fody/Virtuosity)

    Install-Package Virtuosity.Fody

Notice `FodyWeavers.xml` will now look like this:

    <?xml version="1.0" encoding="utf-8" ?>
    <Weavers>
        <Virtuosity/> 
    </Weavers>

### 3. Build

Now have a look at your assembly in your favourite decompiler. All members will now be virtual.