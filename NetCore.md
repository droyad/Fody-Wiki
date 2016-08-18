# .NET Core

*NB: Not all Weavers have been tested with .NET Core, refer to each Weaver's documentation.*

### 1. Reference dotnet-fody

In the `tools` section of your `project.json` add a reference to `dotnet-fody`, specify `import` of `net452`. For example:

    "tools": {
        "dotnet-fody": {
        "version": "0.0.0", //Replace with latest version
        "imports": "net452"
        }
    },

### 2. Add a post compile script

Add the following to your `project.json`:

    "scripts": {
        "postcompile": "dotnet fody %compile:ResponseFile%"
    }

Do not change the command, the dotnet compiler will substitute the response file for you.

### 3. Reference the Fody Weaver

If your project does not need to reference any assemblies in the weaver package, add the package to the `tools` element. 
For example, for the Virtuosity weaver:

    "tools": {
        "Virtuosity.Fody": "0.0.0" // Replace with latest version
    },

If however you do need to reference an assembly (for example for attributes), add the package to the `dependencies` element.
For example, for the Obsolete Weaver:

    "dependencies": {
        "Obsolete.Fody": "0.0.0" // Replace with latest version
    },

If you are unsure, add to the `tools` element, and then switch when you need a type in that package.

If the package restore fails, you may need to import `dnxcore50` into your framework. For example:

    "frameworks": {
        "netcoreapp1.0": {
            "imports": [ "dnxcore50" ]
        }
    },

### 4. Add FodyWeavers.xml

Add a `FodyWeavers.xml` file to the root of your project, and add an element for each Weaver you want to run, for example:

    <Weavers>
        <Virtuosity></Virtuosity>
        <Obsolete></Obsolete>
    </Weavers>