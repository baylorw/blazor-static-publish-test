# blazor-static-publish-test
Test to see if i know how to publish a Blazor WebAssembly Standalone Apps.

Steps
1. Create a project of type Blazor WebAssembly Standalone App. _Not_ Blazor WebApp, which was my original problem.
1. Modify wwwroot/index.html to change base href= to the repository name (needed for relative links in the app to work). Has to both start and end with / (per https://learn.microsoft.com/en-us/aspnet/core/blazor/host-and-deploy/app-base-path?view=aspnetcore-10.0). This will make it not work locally/in IDE though, so that's weird.
1. Modify the file Properties/launchSettings.json and add (for both http and https if you have them) the lines:       `"commandLineArgs": "--pathbase=/my-app-name","launchUrl": "my-app-name",`. There's a starting / on the first, no / on the second. And it matters. 
1. Add to wwwroot a blank file named .nojekyll (otherwise GitHubPages deploys using Jekyll which doesn't publish directories that start with underscores such as _framework).
1. Create a new GitHub repository in a new local folder (_not_ in the one i wrote the app in since we aren't checking in the app source files, we're checking in the published output files).
1. In Visual Studio, Build->Publish.
1. Copy the files from the Publish director's wwwroot subdirectory into the repository directory.
1. Check in and push the files.
1. In GitHub, go to the repo->Settings->Pages.
1. Switch Source to GitHub Actions. The default page publishing process is cool but it doesn't handle apps that use relative URLs for some reason.
1. Click the button to make an action file not using Jekyll.
1. Once you save/checkin that file it will run a job to deploy your site. 
1. Go to your GitHubPages site and then /repo_name.

Figuring out this process using official docs, Stack Overflow, YouTube videos and Google AI took hours. It was sooooo painful. Maybe i should have been a dentist. Or one of those guys who sells hot dogs on the street corner.
