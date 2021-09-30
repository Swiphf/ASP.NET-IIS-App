# IIS Web Application

## Part 1: Creating The ASP.NET Core Project

1. **Open** Visual Studio 2019.
2. **Create** new project.
3. **Choose** "ASP.NET Core Web App" (exactly).
4. **Choose** a name for your application.
5. **Click** "Next".
6. For "Target Framework" **pick** ".NET 5.0".
7. For "Authentication Type" **pick** "None".
8. Make sure to **uncheck** "Configure for HTTPS".
9. **Click** "Create".

## Check csproj content

1. In the Visual Studio, in the solution explorer, **find** your project and **right-click** on it, a drop-down menu
   will be opened. **Click** "Open folder in file explorer". A folder should open containing the project's files.
2. In the project's file folder there should be a file named <YourProjectName> with a ".csproj" extension.  **Open** it with "Notepad"
   or "Notepad++". 
3. The file content should look like this:
  ```
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>

```
  
## Add "Newtonsoft.Json"
  
1. In the Visual Studio, **Click** the "Tools" tab at the top, a dropdown should open. **Click** "Nuget Package Manager" --> "Manage Nuget
   Packages For Solution...".
2. **Switch** to the "Browse" tab.
3. In the search bar, **type** "newtonsoft", **find "Newtonsoft.Json"** and **install** it to your project by ticking the checkboxes 
   indicating which projects should contain the package, (I would recommend ticking all of them for our case), and **Click** "install".
        
## Check csproj Content Again
  
1. **Open** the csproj file as mentioned and described before.
2. You will **notice** some code has been added to the content of the file and it should look like this (might be a differet version):

  ```
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="13.0.1" />
  </ItemGroup>
  ```    
  
## Resore Nuget Packages
  
1. In The Visual Studio, in the "Solution Explorer", **Right-click** on the solution. A drop-down menu should open.
   **Click** "Restore NuGet Packages".
2. **Wait** for the "Output" tab at the bottom to show "Finished".
  
## Compile (Rebuild) The Project
  
1. In The Visual Studio, in the "Solution Explorer", **Right-click** on the solution. A drop-down menu should open.   
   **Click** "Rebuild Solution".
2. **Wait** for the "Output" tab at the bottom to show "1 Succeeded".
  
## Check the source folder for changes
  
1. **Open** the source code files of your project as described above.
2. **Notice** that the "obj" folder has been modified, and the "bin" folder's content has been modified as well.
  
## Publish Your Application
  
1. In The Visual Studio, in the "Solution Explorer", **Right-click** on the project. A drop-down menu should open.   
   **Click** "Publish".
2. A menu with some options should open. **Choose** "Folder" and **click** "Next".
3. **Click** "Finish".
3. On the top-right of the window just opened, **click** "Publish".
  
  
# Part 2: Create website on your Microsoft machine 
  
## Add IIS To Your Windows Server
   
1. In your windows machine, **click** the search bar on the bottom left, **type** "Turn windows features on or off" and **click** it.
2. In the list shown, **Tick** "Internet Information Services" and **click** "OK".
3. In order to use IIS **type** "Internet Information Services (IIS) Manager" in the search bar and "click" it.
  
## Create a New IIS Application Pool
  
1. In the IIS Manager, to the left, you should see a files "tree" named "Connections". There should be a row with the name of your computer.
   **Double click** it 
2. You should see a row named "Application Pools". **Right-click** it and then **click** "Add Application Pool".
3. In the small window just opened, **Type** a name of your choosing. Also, make sure to **choose** "No Managed Code" in the ".NET CLR Version".
   **Click** "OK".
  
## Enable files transfer between your local PC and the Windows Machine
  
#### Assuming you are using RDP to access your windows machine:
  
1. In the search bar, at the bottom left of your screen, **type** "Remote Desktop Connection" and **click** it.
2. A small window should open. **Click** "Show Options".
3. **Switch** to "Local Resources" tab.
4. **Click** the "More" button at the bottom.
5. **Extend** the "Drives" row by click on the small "+" next to it.
6. **Choose** a drive that will act as a common folder between your PC and the windows machine. (If you dont have another drive option you can
   plug in a USB device and use it the same way). **Click** "OK".
7. **Click** "Connect".
8. The common folder should be visible when clicking "This PC".    
  
## Create Website
  
1. In the IIS Manager, in the "Connections" mentioned above, **right-click** on "Sites" and **click** "Add Website".
2. In the "Site name" text input, **type** a name for your site.
3. In the "Application Pool" text input, **use** the "Select" button, **Select** the application pool you have created before and
   then **Click** "OK".
4. In the "Physical path" text input, **click** the three dots at the right of the input. In the path: "C:\inetpub\wwwroot\BootcampWebsite", 
   **Create** a new folder with a name of your choosing.
5. In the "Port" text input **Type** 5100.
6. **Click** "OK". You should be able to see your website with the name you chose in the "Connections" tree to the left.        
  
### Transfer Source Files Of Your Website Into The Windows Machine
  
1. In your PC **open** your website's source files folder as described above.
2. In the "bin\Release\net5.0\publish" folder, you should see some files. **Copy** all of them to the common folder mentioned above in your PC.
3. In the windows machine, the files should be visible in the common folder. **Copy or Move** all of them to a local location in the windows machine.
   Highly Recommended to this path:"C:\inetpub\wwwroot\<folderNameThatYouCreatedAbove>".

## Browse To `http://localhost:5100/` From Your Microsoft Machine
  
1. In the "Connections" files tree to the left --> Sites, **click** your website's name.
2. To the right, your should be able to see a menu. In this menu there should be a "Browse website" tab. Under it, a link: "Browse *:5100" (http).
   **Click** it.
3. Your website is complete and should show you the default html page provided in ASP.NET Core.
  
