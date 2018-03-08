Simple repro of dotnet restore behavior on 2.1 preview 1

Where dotnet restore throws error when project files are missing. This seems to have been a warning in ealier versions

This breaks, among other things the default Visual Studio Docker tools Dockerfile's that only copies the .sln file and .csproj for the given image
