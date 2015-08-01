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

Now have a look at your assembly in your favorite decompiler. All members will now be virtual.

## References

Most Fody Addin references are only metadata assemblies with attributes. As such they, usually, should not be deployed.

Most Addins will handle this properly via nuget install.ps1. However some versions of Nuget do not support install.ps1. In this case you will need to perform two actions.

### 1. Add the Addin

Manually add the addin name to the `FodyWeavers.xml` as outlined above

### 2. Set the reference to "not be copied"

In a standard .net project you can do this by setting the reference to be `Copy Local = False`.

In the new `project.json` projects you will need to edit the reference manually and add a `"options": "dev"` to the attribute of the target dependency.

So, for example, initially the reference till look like this

    "PropertyChanged.Fody": "1.50.2"

And you will change it to this

    "PropertyChanged.Fody": {"version": "1.50.2", "options": "dev"}