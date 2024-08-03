# Windows
## Visual studio
When Projucer has generated a project for you, the Visual Studio Solution is generated in your project folder under `{Platform}\{VisualStudioVersion}` where Platform is 32 or 64 (x86 ot x64) bit and VisualStudioVersion is the flavor of Visual Studio you use.
### 1. **Create a project**
1. Open Visual Studio.
2. Select `File` > `New` > `Project...`.
3. Choose `Console App` (under Visual C++ or similar).
4. Name your new project (e.g., `Tests`) and specify its location.
5. Click `Create`.

It will add a Tests folder to your project. Inside it you will find the Tests.sln and another folder called Tests. In the subfolder (ProjectRoot/Tests/Tests) you will find Tests.vcxproj. This is the path that your include folders will be relative to.

### 2. **Configure the project**
Your configuration should be almost the same as the StandAlonePlugin project in your regular project.

1. Open your test project.
2. Right click on Tests > Properties.
3. Under `VC++ Directories`,  add `$(SolutionDir)$(Platform)\$(Configuration)\Shared Code`.
4. Under `C/C++ > General > Additional Include Directories`, copy the information in your regular projects StandAlonePlugin. 
4. Under `C/C++ > Preprocessor > Preprocessor Definitions`, copy the information in your regular projects StandAlonePlugin. (This step may be unecessary, you can try without it.)
5. Under `Linker > Input`, add `YourProject.lib` so that the resulting field is `YourProjectLib;%(AdditionalDependencies)`.
6. Add `Microsoft.Web.WebView2` from the Nuget Package Manager. (Optional, only needed if you're using webviews.

# Troubleshooting

### 1. Copy StandAloneApp settings
1. Open your regular project.
2. Right click on `StandAlonePlugin > Properties`.
2. Under `VC++ Directories`, compare its entries with the ones in the tests project. Look for suspicious differences. 
3. Under `C/C++ > All Options`, compare its entries with the ones in the tests project. Look for suspicious differences.
4. Under `Linker > All Options`, compare its entries with the ones in the tests project. Look for suspicious differences.
