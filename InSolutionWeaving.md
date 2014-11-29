# How to write weaving code inside a solution.

## Introduction

Often it is necessary to have weaving code specific to a solution. In this case it is desirable to have that code exist in the same solution it is editing.

## How to weave inside a solution 

Fody will look for a binary named `Weavers.dll` inside the directory `Weavers\bin`. This directory must be in the solution root. If there are multiple matches found (e.g. `Weavers\bin\Debug\Weavers.dll` and `Weavers\bin\Release\Weavers.dll`) then it will use the most recently-modified version, irrespective of your active build configuration.

The [Integration](https://github.com/Fody/Fody/tree/master/Integration) directory provides examples of this - refer to `WithOnlyInSolutionWeaver` and `WithNugetAndInSolutionWeavers`.

To enable in-solution weaving:

  1. Add a project named 'Weavers' to your solution. The assembly name for the project must be `Weavers` and it must be in a directory named "Weavers".

  2. Add a class named `ModuleWeaver` to the project. See [ModuleWeaver](ModuleWeaver).  

     _Note: The `ModuleWeaver` class will be automatically used in every Fody-enabled project in the solution. It is also possible to select specific weavers for specific projects; to do this, choose a different class name and refer to step 4._

  3. Change the solution build order so the 'Weavers' project is built before the projects using it.  

     _Note: Do not add a project reference._

  4. If a weaver class is named something other than `ModuleWeaver`, edit the `FodyWeavers.xml` file in the projects where it should be used. For example, if the class name is `NamedWeaver`:

     ```xml
     <Weavers>
       <NamedWeaver />
     </Weavers>
     ```