# blazor-static-publish-test
Test to see if i know how to publish a Blazor WebAssembly Standalone Apps.

Steps
1. Create a project of type Blazor WebAssembly Standalone App. _Not_ Blazor WebApp, which was my original problem.
1. Modify wwwroot/index.html to change base href= to the repository name (needed for relative links in the app to work).
1. Add to wwwroot a blank file named .nojekyll (otherwise GitHubPages creates Jekyll stuff that interferes with the app).
1. Create a new GitHub repository in a new local folder (_not_ in the one i wrote the app in since we aren't checking in the app source files, we're checking in the published output files).
1. In Visual Studio, Build->Publish.
1. Copy the files from the Publish director's wwwroot subdirectory into the repository directory.
1. Check in and push the files.
1. In GitHub, go to the repo->Settings->Pages.
1. Set the Branch to main and root then click Save.
1. Go to your GitHubPages site and then /repo_name.
