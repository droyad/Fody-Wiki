# Weaving Task Options

## AssemblyPath 

The path to the assembly to process. 

*Required*

    <Fody.WeavingTask ... AssemblyPath="@(IntermediateAssembly)" />

## SolutionDir 

The path to the directory containing the solution. 

*Required*

    <Fody.WeavingTask ... SolutionDir="$(SolutionDir)" />

## ProjectPath 

The path to the current project file. 

*Required*

    <Fody.WeavingTask ... ProjectPath="$(ProjectPath)" />

## References 

A comma separated list of paths to assembly references. 

*Required*

    <Fody.WeavingTask ... References="@(ReferencePath)" />

## KeyFilePath 

The path to the strong name key of the assembly. 

*Optional.* Uses the 'AssemblyOriginatorKeyFile' and 'SignAssembly' nodes of the target project to attempt to derive the path.

    <Fody.WeavingTask ... KeyFilePath="$(SolutionDir)MyKeyFil.snk" />