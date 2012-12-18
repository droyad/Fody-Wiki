# How to manually add to a project

**Setup can be simplified by installing the [Visual Studio package](http://visualstudiogallery.msdn.microsoft.com/074a2a26-d034-46f1-8fe1-0da97265eb7a)**


However if you want to manually set up Fody...

  * Get the latest VSIX from here http://visualstudiogallery.msdn.microsoft.com/074a2a26-d034-46f1-8fe1-0da97265eb7a
  * Unzip the download (the VSIX is actually a zip). 
  * Place the files from 'VSIXUnzipPath\ContentFiles\Fody' where Visual Studio/Mono Develop can find it. In my case it is in a directory called `Tools\Fody` at the root of my solution. 
  * Import `Fody.targets` to your project.

eg  

    <Project>     
        <Import Project="$(SolutionDir)\Tools\Fody\Fody.targets" />
    </Project>
  
  * Add a "FodyWeavers.xml" to the project. There is a empty one in 'VSIXUnzipPath\ContentFiles'
  * Add a weaver. See "Add the weaver nuget package" in  [SampleUsage](SampleUsage)
  * Build. 