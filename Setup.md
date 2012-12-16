# How to manually add to a project

**Setup can be simplified by installing the [Visual Studio package](http://visualstudiogallery.msdn.microsoft.com/074a2a26-d034-46f1-8fe1-0da97265eb7a)**


However if you want to manually set up Fody...

  * Get the latest download https://s3.amazonaws.com/Fody/
  * Unzip the download. Place the files from 'MSBuild' where Visual Studio can find it. In my case it is in a directory called `Tools\Fody` at the root of my solution. 
  * Import `Fody.targets` to your project.

eg  

    <Project>     
        <Import Project="$(SolutionDir)\Tools\Fody\Fody.targets" />
    </Project>
  
  * Add a "FodyWeavers.xml" to the project. 
  * Add a weaver. See "Add the weaver nuget package" in  [SampleUsage](SampleUsage)
  * Build. 