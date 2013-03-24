# How to manually add to a project

If you want to manually set up Fody...

  * Get the nuget package https://nuget.org/packages/Fody/
  * Unzip the download (the package is actually a zip). 
  * Place the files files in the root where Visual Studio/Mono Develop can find it. In my case it is in a directory called `Tools\Fody` at the root of my solution. 
  * Import `Fody.targets` to your project.

eg  

    <Project>     
        <Import Project="$(SolutionDir)\Tools\Fody\Fody.targets" />
    </Project>
  
  * Add a "FodyWeavers.xml" to the project. There is a empty one in 'VSIXUnzipPath\ContentFiles'
  * Add a weaver. See "Add the weaver nuget package" in  [SampleUsage](SampleUsage)
  * Build. 