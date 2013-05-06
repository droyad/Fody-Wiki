## ModuleWeaver Class 

 * The class should be public, instance and not abstract.
 * Have an empty constructor. 
 * A `ModuleDefinition` property that will be populated during build. It will contain the Cecil representation of the assembly being built
 * A `Execute` method with the signature that is called as part of a build after the properties have been set.

For example the minimum class would look like this

    public class ModuleWeaver
    {
        public ModuleDefinition ModuleDefinition { get; set; }

        public void Execute()
        {
            ModuleDefinition.Types.Add(new TypeDefinition("MyNamespace", "MyType", TypeAttributes.Public, ModuleDefinition.Import(typeof(object))));
        }
    }

There are also a number of optional properties that will be populated before 'Execute' is called.

 * A `Config` property that will contain the full element xml from FodyWeavers.xml.
 * `LogInfo`, `LogWarning` and `LogError` delegates for logging informational, warning and error messages respectively. 
 * `LogWarningPoint` and `LogErrorPoint` delegates for logging warning and error messages at a specific point in the code. Using these delegates will allows users to navigate to the code position via the Visual Studio "Error List"
 * An `AssemblyResolver` property that will contain a `Mono.Cecil.IAssemblyResolver` for resolving dependencies.
 * An `DefineConstants` property that will contain all the compile time constants that have been defined as part of the build.
 * An `ProjectDirectoryPath` property that will contain the directory path of the project being processed.
 * An `AssemblyFilePath` property that will contain the path to the assembly being processed.
 * An `AddinDirectoryPath` property that will contain the directory path if the current addin.
 * An `SolutionDirectoryPath` property that will contain the directory path if the current solution. 

For example

    public class ModuleWeaver
    {
        public XElement Config { get; set; }
        public Action<string> LogInfo { get; set; }
        public Action<string> LogWarning { get; set; }
        public Action<string, SequencePoint> LogWarningPoint { get; set; }
        public Action<string> LogError { get; set; }
        public Action<string, SequencePoint> LogErrorPoint { get; set; }
        public IAssemblyResolver AssemblyResolver { get; set; }
        public ModuleDefinition ModuleDefinition { get; set; }
        public List<string> DefineConstants { get; set; }
        public string AssemblyFilePath { get; set; }
        public string ProjectDirectoryPath { get; set; }
        public string AddinDirectoryPath { get; set; }
        public string SolutionDirectoryPath { get; set; }

        // Init logging delegates to make testing easier
        public ModuleWeaver()
        {
            LogInfo = m => { };
            LogWarning = m => { };
            LogWarningPoint = (m,p) => { };
            LogError = m => { };
            LogErrorPoint = (m, p) => { };
        } 

        public void Execute()
        {
            ModuleDefinition.Types.Add(new TypeDefinition("MyNamespace", "MyType", TypeAttributes.Public));
        }
    }