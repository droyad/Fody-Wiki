If you are seeing this page then one of your projects has been updated to the new Fody nuget.

Steps you shoould follow

* Ensure the Fody nuget has been applied to all projects in the current solution. The nuget will take care of converting projects from the VSIX approach to the nuget package approach.
* Avoid using the Fody VSIX Enable/Disable for any projects in this solution.
* Manually delete `Tools/Fody` from both your local copy and source control