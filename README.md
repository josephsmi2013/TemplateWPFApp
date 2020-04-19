# TemplateWPFApp
Basic template for creating WPF apps with an API and SQL DB

# Setup Instructions

# Create GitHub Repository
# Purpose
Provides storage facilities for the solution
# Steps
1.	Login to github.com/new
2.	Create a new repository name/description
3.	Make private or public
4.	Include a readme (this makes cloning easy)
5.	Add a .gitignore file so Github can ignore certain temp and build files from Vis Studio
6.	Add a license (or explicitly restriction use and distribution in the readme)
7.	Select “Create Repository” button
8.	Copy the download link from Github
9.	Now, right click in the windows explorer parent folder location
10.	Choose “Git Bash Here” (requires GIT is installed)
11.	In the command window type “git clone “ [paste link to GIThub repo]
12.	Next, create a new Visual Studio project. Search “blank solution” as the type
13.	Browse to the parent folder of the folder created by GIT. Select OK
14. Back in VS, select Team Explorer. Right click the new solution file and select for staging
15. Once files are staged (bundled), they can be commited locally using "Commit Staged"
16. After local commit. Files can be syned to the repo using "Sync"
16. Note: Syncing does a pull and then a push of staged files
17. Note: A fetch will show you which files from the repo have changes without forcing a modification

# Create Web API
# Purpose
Create public endpoints for retrieving and posting data to a custom application
# Steps
1.	From Visual Studio, create new project
2.	Select the ASP.net Web Application template
3.	Select the Web API project
4.	For authentication, Enable Individual User Accounts
5.	Leave all other options default
6.	Select name and location for the application

# Configure Swagger
# Purpose
Provides Web API documentation and ability to test the API
# Steps
1.	In Solution Explorer, right click “References”  “Manage Nuget Packages”
2.	Search for Swashbuckler (must be exact), choose to install, restart maybe required
3.	Repeat, except this time use the “Updates” tab of Nuget Packages to install latest updates
a.	May not want to Bootstrap 4.0 or later since I hear it take a lot of new configuration
4.	Run solution before modifying any code as a quick test
5.	Copy the classes AuthTokenOperation.cs, AuthOperationFilter.cs and SwaggerConfig.cs into the new project
6.	Run the solution, navigate to [AppURL:port]/swagger
7.	Retrieve a token from the Auth section in order to test AuthTokenOperation.cs
8.	Use the token in any API call to test the AuthOperationFilter.cs 
a.	Remember the syntax is “Bearer ” [token] 

# Create Database
# Purpose
Add a DB project to the solution for storing custom data in our application
# Steps
1.	Right click Solution and choose Add  Add New Project
2.	Search for “SQL Server database project”
3.	Name the database project
4.	Add new root folder “dbo” (schema name) to the Database project
a.	Add subfolders “Tables”, “Views”, “Stored Procedures”
5.	Add new root folder “PublishLocations” (to store scripts?) to the Database project
6.	Right click database project and select “Publish”
7.	Select “Edit” button and browse. Select “Local” then, “MSSQLDB”. Keep other defaults
a.	Select ok. This should create the connection string
8.	Give database a name. Can be same as database project name
9.	Select “Save Profile As”, choose the “PublishLocations” folder. Keep filename the same.
10.	Should be able to use the SQL Server Object browser to review now


