# How To Write An Add-in

## How to deploy Addins 

Addins are deployed as single assemblies. These assemblies can be can be deployed directly to one of the [AddinSearchPaths](AddinSearchPaths) or using nuget [DeployingAddinsAsNugets](DeployingAddinsAsNugets).

## The assembly

 * The assembly must be suffixed with ".Fody". 
 * Any dependencies (excluding Mono Cecil) should be combined using  [ILMerge](http://research.microsoft.com/en-us/people/mbarnett/ilmerge.aspx) and the `/Internalize` flag.
 * The assembly should contain a class named 'ModuleWeaver'. Namespace does not matter.

## ModuleWeaver Class 

Add a class named 'ModuleWeaver' to the project. See [ModuleWeaver](ModuleWeaver)

## FodyWeavers.xml

This file exists at a project level and is used to pass configuration to the 'ModuleWeaver'.

So if the FodyWeavers.xml file contains the following

    <?xml version="1.0" encoding="utf-8" ?>
    <Weavers>
      <Virtuosity MyProperty="PropertyValue"/>
    </Weavers>

The Config property of the ModuleWeaver will be an XElement containing

    <Virtuosity MyProperty="PropertyValue"/>