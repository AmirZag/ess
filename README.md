# ESS

A .NET solution (ESS) with Docker Compose and PowerShell tooling for local development and containerized deployment.

## Table of contents
- [About](#about)
- [Features](#features)
- [Architecture](#architecture)
- [Requirements](#requirements)
- [Quick start (Docker)](#quick-start-docker)
- [Quick start (Local / Visual Studio / dotnet CLI)](#quick-start-local--visual-studio--dotnet-cli)
- [Build & test](#build--test)
- [Configuration](#configuration)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## About
This repository contains a .NET solution (ESS.sln) with projects implemented in C#. It includes Docker Compose files to run services locally in containers, and PowerShell scripts to assist with automation or assets. Use this README to get started developing, running, and testing the solution.

## Features
- Solution organized in a Visual Studio / .NET solution (`ESS.sln`)
- Docker Compose based local environment for easy startup
- PowerShell helpers for common tasks (e.g. image saving)
- Cross-platform development using `dotnet` CLI or Visual Studio / VS Code

## Architecture
- Solution root: `ESS.sln` - contains the projects that make up the application.
- `src/` - application source projects (services, libraries, etc.).
- `test/` - unit and integration tests.
- `docker-compose.yml` / `docker-compose.override.yml` - containers to run the system locally.
- PowerShell scripts for build / helper tasks (e.g. `save-images.ps1`).

(Adjust the above if your solution contains additional folders or microservices — this is a general outline based on the repository layout.)

## Requirements
- .NET SDK (recommended: .NET 6 or later)
- Docker & Docker Compose (for containerized development)
- Git
- (Optional) Visual Studio, Visual Studio Code or another .NET-capable IDE

## Quick start (Docker)
Start the full system using Docker Compose:

1. Build and start containers:
   - Using Docker Compose V2:
     docker compose up --build
   - Using Docker Compose V1:
     docker-compose up --build

2. Open logs in your terminal or visit service endpoints configured in `docker-compose.yml`.

3. To stop and remove containers:
   docker compose down

Docker Compose will build C# projects into images and run them, so you do not need to build locally first.

## Quick start (Local / Visual Studio / dotnet CLI)
To run locally without Docker:

1. Restore and build
   dotnet restore ESS.sln
   dotnet build ESS.sln -c Debug

2. Run a specific project
   - Open `ESS.sln` in Visual Studio and run the desired startup project, or
   - From the command line:
     dotnet run --project src/<YourProjectName> --configuration Debug

Replace `<YourProjectName>` with the actual project folder/name inside `src/`.

## Build & test
- Restore packages:
  dotnet restore ESS.sln

- Build solution:
  dotnet build ESS.sln -c Release

- Run tests:
  dotnet test ESS.sln --no-build --verbosity normal

Adjust commands and project paths to match your folder structure if needed.

## Configuration
- Environment-specific settings are typically provided via appsettings.json files inside each project, or via environment variables when running in Docker.
- Docker Compose overrides may be present in `docker-compose.override.yml` for development-time settings.
- Use `launchSettings.json` for debugging profiles in Visual Studio / VS Code.

## Contributing
Contributions are welcome. Suggested workflow:
1. Fork the repository.
2. Create a feature branch: `git checkout -b feat/short-description`.
3. Make changes and add tests.
4. Run `dotnet build` and `dotnet test`.
5. Open a Pull Request describing your changes.

Please follow any code style or commit conventions documented in repository files. If you want, add an ISSUE_TEMPLATE or PR_TEMPLATE to standardize contributions.

## License
See `LICENSE.txt` in the repository root for license details.

## Contact
If you have questions or need help, open an issue or contact the maintainers via the repository.
