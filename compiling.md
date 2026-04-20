*If a law is unjust, a man is not only right to disobey it, he is obligated to do so.*

## how to add support for .mesh and compile yourself
work in progress

### prerequisites
Visual Studio Code

Git

.NET 6.0 SDK (v6.0.428) <-- this is the SDK, not .NET runtime.

### steps
open Visual Studio Code and click on Clone Git Repository... underneath Start then paste repo link and choose somewhere to put it.

... or download fishstrap source to your computer by clicking on the big green code button and clicking on download ZIP, then unzip it and open it in Visual Studio Code

go to `Bloxstrap\bootstrapper.cs` open it and ctrl+f to find ".mesh", it should look like the example below

```C#
                if (relativeFile.EndsWith(".mesh"))
                {
                    App.Logger.WriteLine(LOG_IDENT, $"Skipping file: {relativeFile}");
                    continue;
                }
```

then delete or comment out the offending code

close `bootstrapper.cs` and save

open the terminal and type `git submodule update --init --recursive` to download contents of submodule wpfui

type `dotnet publish -c Release -r win-x64 --no-self-contained /p:PublishSingleFile=true` into the terminal

wait until it's done, then go pick up your .exe at `Bloxstrap\bin\Release\net6.0-windows\win-x64\publish`

**make sure you actually go to the `\publish` folder to get your .exe and not it's parent folder**

run the .exe and add mesh files in the mod folder just to make sure that it works first

publish your own binary to your own fork for proliferation, or on a different source control platform for decentralization.
