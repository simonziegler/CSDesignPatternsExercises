# C# Basics
Simon Ziegler, 28 August 2023

## What are C# and .NET?
C# is a "managed language" that runs under the [.NET environment](https://learn.microsoft.com/en-us/dotnet/). .NET is a program that Microsoft publish for major tech operating systems, including Windows, macOS, Linux, iOS and Android. The `dotnet` program is published in two varieties: (i) the "runtime" which is capable of running compiled .NET assemblies and (ii) the Software Development Kit ("SDK") which compiles code to assemblies, performs publishing tasks and can also run assemblies. The SDK is downloaded with Visual Studio, and VS uses the SDK to build and run your code.

C# is derived from the earlier groundbreaking languages C and C++, which date from the early '70s and early '80s respectively. C is a very low level language with a limited core instruction set, where higher level functionality is introduced by incorporating libraries into systems. Being a low level language it's "close to the metal" meaning that there's a tight relationship between what you code and the compiled machine code. This makes C programs extremely fast (important at a time when computers were very low powered) but also prone to unreliability since programmers had free rein to write to any memory address. C++ added object orientation to C, and generally C++ compilers are used for compiling C code. Since C/C++ compile to machine code for the specific microprocessor on the machine where the code is compiled, the compiled programs are not portable to other architectures, requiring compilation separately for any additional architecture.

Being a managed language, C# resolves a lot of problems associated with low level C/C++:
1. It is a "compile once, run anywhere" model, given that all you need to run your assembly for any given architecture is the ability to install the .NET runtime.
2. .NET manages memory for you. There's no need to allocate and de-allocate large areas of memory as required in C/C++, because this is done for you. Unlike C/C++ if you try to access an index of an array beyond that array's bounds, you will get a runtime exception.
3. There are no pointers, so again no ability to access areas of memory to which you should have no access.

So:
- C# is the programming language (also F# and VB.NET).
- .NET is the platform and compiles/publishes C# to .NET assemblies, then runs those assemblies.

## Introduction to the `dotnet` command line tool and how it works with a CSPROJ file
The [.NET Command Line Interface](https://learn.microsoft.com/en-us/dotnet/core/tools/) ("CLI") is invoked by running the `dotnet` command from the command line. On windows the command line is run either from the command shell or better by running powershell - both from the start menu. Examples include:
- `dotnet build T01_CollectionPerformance.csproj`
- `dotnet restore T01_CollectionPerformance.csproj`
- `dotnet run T01_CollectionPerformance.csproj`

Note how in each case we are referencing the `CSPROJ` ("C # project file") file, which determines how a project should be built by .NET. The project file referenced above has the contents below. At some stage you will need to know how to configure these files.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Project Sdk="Microsoft.NET.Sdk">									<!-- Determines the SDK to be used -->

	<PropertyGroup>
		<OutputType>Exe</OutputType>								<!-- Determines that the output is an executable file -->
		<TargetFramework>net7.0</TargetFramework>					<!-- Specifies .NET version 7, the current version released in November 2022 (.NET 8 is imminent) -->
		<ImplicitUsings>enable</ImplicitUsings>						<!-- Google it -->
		<Nullable>enable</Nullable>									<!-- Google it -->
	</PropertyGroup>

	<ItemGroup>
		<PackageReference Include="Humanizer" Version="2.14.1" />	<!-- Imports the Humanizer Nuget package v 2.14.1 -->
		<PackageReference Include="morelinq" Version="3.4.2" />		<!-- Imports the morelinq Nuget package v 3.4.2 -->
	</ItemGroup>

</Project>
```

Also see the considerably more complex [CSPROJ](https://github.com/Material-Blazor/Material.Blazor/blob/main/Material.Blazor/Material.Blazor.csproj) file built by my development partner [@MarkStega](https://github.com/MarkStega) for our Material.Blazor OSS project.

## Using `dotnet` with GitHub workflows
[GitHub](https://github.com/) (or its competitors [GitLab](https://about.gitlab.com/), [Bitbucket](https://bitbucket.org/) etc.) is a source code repository using the Git source code control system. This project is hosted on GitHub. GitHub offers much more than just source code control, and is a complete "Devops" envronment for software development. This includes automated software build and deployment using GitHub workflows. A (rather complex) [example](https://github.com/Material-Blazor/Material.Blazor/blob/main/.github/workflows/GithubActionsRelease.yml), again written by Mark, deploys releases of Material.Blazor, both creating and publishing the project's [Nuget package](https://www.nuget.org/packages/Material.Blazor), and building and deploying the [website](https://material-blazor.com/).

## Overall C# program structure
Bringing the previous sections 
## C# language
### Main method
### Language constructs
### Interfaces
### Generics
### Collections and collection performance
### LINQ