# TemplateWPFApp
Basic template for creating WPF apps with an API and SQL DB

# Setup Instructions

# Create GitHub Repository
# Purpose
Provides storage facilities for the solution
# Steps
* Login to github.com/new
* Create a new repository name/description
* Make private or public
* Include a readme (this makes cloning easy)
* Add a .gitignore file so Github can ignore certain temp and build files from Vis Studio
* Add a license (or explicitly restriction use and distribution in the readme)
* Select “Create Repository” button
* Copy the download link from Github
* Now, right click in the windows explorer parent folder location
* Choose “Git Bash Here” (requires GIT is installed)
* In the command window type “git clone “ [paste link to GIThub repo]
* 1Next, create a new Visual Studio project. Search “blank solution” as the type
* Browse to the parent folder of the folder created by GIT. Select OK
* Back in VS, select Team Explorer. Right click the new solution file and select for staging
* Once files are staged (bundled), they can be commited locally using "Commit Staged"
* After local commit. Files can be syned to the repo using "Sync"
* Note: Syncing does a pull and then a push of staged files
* Note: A fetch will show you which files from the repo have changes without forcing a modification

# Create Web API
# Purpose
Create public endpoints for retrieving and posting data to a custom application
# Steps
* From Visual Studio, create new project
* Select the ASP.net Web Application template
* Select the Web API project
* For authentication, Enable Individual User Accounts
* Leave all other options default
* Select name and location for the application
* Now, right click "References" in solution explorer
* Select "Manage Nuget Packages"
* From the "updates" tab. Select all (except bootstrap as v4 may have breaking changes). Use update button
* Agree to all (may require a restart)
* Run application to test connectivity/updates
* Stop the application. Use the IIS Express dropdown to edit project properties
* In the Web Menu --> Project Url, modify "https" to be "http". 
* Close to create a new virtual directory for http
* Start the app and use http for navigation
* Note: App_Start folder contains Config files with numerous settings that can be changed/updated
* Use Postman to register a new user. 
* This will require using a POST method, the register endpoint "/api/account/register", passing params in the body using raw data formatted as JSON
* Note: The body JSON params can be copied from the API doc provided
* Test the new user by api/values. This is an authorized endpoint and will require a token
* Get a token from http://localhost:port/token. This will require three parameters be passed as x-www-form-encoded
* param = "grant_type", value = "password"
* param = "username", value = [username of registered user]
* param = "password", value = [password of registered user]
* Pass these as a Get request. It will return a token
* Now, create a Get request to localhost:port/api/values
* Pass a single header param called "Authorization". The value will be "Bearer " + [Authtoken]

# Configure Swagger
# Purpose
Provides Web API documentation and ability to test the API
# Steps
* In Solution Explorer, right click “References” --> “Manage Nuget Packages”
* Search for Swashbuckler (must be exact), choose to install, restart maybe required
* Repeat, except this time use the “Updates” tab of Nuget Packages to install latest updates
* May not want to Bootstrap 4.0 or later since I hear it take a lot of new configuration
* Run solution before modifying any code as a quick test
* Copy the classes AuthTokenOperation.cs, AuthOperationFilter.cs and SwaggerConfig.cs into the new project
* Run the solution, navigate to [AppURL:port]/swagger
* Retrieve a token from the Auth section in order to test AuthTokenOperation.cs
* Use the token in any API call to test the AuthOperationFilter.cs 
* Remember the syntax is “Bearer ” + [Authtoken] 
* Check In changes using Team Explorer (instructions above)

# Create Database
# Purpose
Add a DB project to the solution for storing custom data in our application
# Steps
* Right click Solution and choose Add --> Add New Project
* Search for “SQL Server database project”
* Name the database project
* Add new root folder “dbo” (schema name) to the Database project
* Add subfolders “Tables”, “Views”, “Stored Procedures”
* Add new root folder “PublishLocations” (to store scripts?) to the Database project
* Right click database project and select “Publish”
* Select “Edit” button and browse. Select “Local” then, “MSSQLDB”. Keep other defaults
* Select ok. This should create the connection string
* Give database a name. Can be same as database project name
* Select “Save Profile As”, choose the “PublishLocations” folder. Keep filename the same.
* Select "Publish". Should be able to use the SQL Server Object browser to review now
* Check In changes using Team Explorer (instructions above)


