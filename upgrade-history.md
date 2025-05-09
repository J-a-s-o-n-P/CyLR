# CyLR .NET Upgrade History

## Project Upgrade from .NET Core 3.1 to .NET 8.0

### Framework Updates
- Changed target framework from `netcoreapp3.1` to `net8.0` in both project files:
  - `/CyLR/CyLR.csproj`
  - `/CyLRTests/CyLRTests.csproj`
- Updated version number to 3.1.0 to reflect the major upgrade

### Package Updates
- Updated NuGet package references:
  - DiscUtils: 0.13.0-alpha → 0.16.13
  - DotNet.Glob: 3.1.0-alpha0009 → 3.1.3 
  - SharpZipLib: 1.0.0 → 1.4.2
  - SSH.NET: 2016.1.0 → 2020.0.2
  - Maintained RawDiskLib at 0.1.4 as it's a specialized library
- Updated test packages:
  - coverlet.msbuild: 2.8.0 → 6.0.0
  - Microsoft.NET.Test.Sdk: 15.8.0 → 17.8.0
  - xunit: 2.4.0 → 2.6.2
  - xunit.runner.visualstudio: 2.4.0 → 2.5.4

### Project Modernization
- Replaced deprecated `PackageLicenseUrl` with `PackageLicenseExpression`
- Replaced deprecated `PackageIconUrl` with `ApplicationIcon`

### Next Steps
After .NET 8 SDK is installed:
1. Run `dotnet restore` to restore packages
2. Run `dotnet build` to verify compilation
3. Run `dotnet test` to verify functionality
4. Create builds for all target platforms

### Benefits of Upgrade
- Improved performance
- Current security patches
- Long-term support (until November 2026)
- Access to newer language features
- Better compatibility with modern development environments

### Dependencies
The raw filesystem access functionality should continue working as:
- The key libraries (DiscUtils, RawDiskLib) are used in a contained way
- The updated DiscUtils package maintains API compatibility 
- No .NET Core 3.1-specific APIs that were removed in .NET 8 are being used