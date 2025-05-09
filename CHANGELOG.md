# CHANGE LOG

## 3.1.0 - 2024-05-09

This version includes a major framework upgrade and dependency updates to modernize the codebase:

### Added
* Upgraded from .NET Core 3.1 to .NET 8.0 for all target frameworks
* Added support for modern .NET 8 features and optimizations
* Improved cross-platform compatibility
* Added Windows x64 and x86 self-contained executables

### Changed
* Updated NuGet dependencies to latest compatible versions:
  * DiscUtils: 0.13.0-alpha → 0.16.13
  * DotNet.Glob: 3.1.0-alpha0009 → 3.1.3
  * SharpZipLib: 1.0.0 → 1.4.2
  * SSH.NET: 2016.1.0 → 2020.0.2
* Updated test packages to latest versions:
  * coverlet.msbuild: 2.8.0 → 6.0.0
  * Microsoft.NET.Test.Sdk: 15.8.0 → 17.8.0
  * xunit: 2.4.0 → 2.6.2
  * xunit.runner.visualstudio: 2.4.0 → 2.5.4
* Replaced deprecated `PackageLicenseUrl` with `PackageLicenseExpression`
* Replaced deprecated `PackageIconUrl` with `ApplicationIcon`
* Improved build process for cross-platform builds
* Fixed nuget.config to use current package sources

### Benefits
* Improved performance and lower memory usage
* Current security patches through November 2026 (LTS)
* Better compatibility with modern development environments
* Faster startup time and reduced package size
* Enhanced cross-platform support

## 2.2.0 - 2020-07-09

This version includes numerous modifications and introduction of new features,
highlighted below:

### Added

* Logging is available, to destinations including the console, a log file, and
  embedded within the resulting archive. The log name is specified with `-l`
  and verbosity is adjusted with `-v` to increase or `-q` to silence.
* Added `CUSTOM_PATH_TEMPLATE.txt` with documentation on how to specify custom
  paths for collection.
* Implemented enumeration of files system contents in the same manner cross
  platform
* Through new FS enumeration, eliminated extra scanning/duplicate collection
  of data within symbolic link directories. Eliminated dependency on the
  `find` binary.
* Enabled the use of globbing patterns within paths. This includes patterns
  such as:
  * `**/*.plist`
  * `/home/*/.*sh_history`
  * `\Windows\Temp\[a-z0-9][a-z0-9][a-z0-9][a-z0-9]\*`
  * `**/Library/*Support/Google/Chrome/Default/History*`
* Enabled the use of regular expressions within paths. This includes full line
  and substring patterns, such as:
  * `.*mawlare.*`
  * `^C:\Windows\Temp\[A-Za-z0-9]{8}\.*$`
  * `^C:\Windows\System32\Config\(SOFTWARE|SYSTEM|SAM|SECURITY).*$`
* Added functionality to allow the user to select whether the existence of a
  custom collection list (`-c`) should be in addition to versus in place of
  the default artifact list. Continues to default to the replacement option
  where it will only collect specified files.
* Modified config file to support specification of path pattern type. Can be
  one of `static`, `glob`, or `regex`. Format should be a tab delimited text
  file with one pattern type and path per line. A line starting with a pound
  character will be ignored.
* Provided status messages to summarize the number of files scanned and paths
  staged for collection.
* Increased documentation of source code.

### Removed

* Removed collection of Windows Search path due to large size on some systems
  (`%PROGRAMDATA%\Microsoft\Search\Data\Applications\Windows`).
  Please use `-c` to re-include as needed.

### Changed

* Edited build scripts to point to C:\Program Files\7z instead of x86 folder
* Improved the default collection paths for Linux platforms.
* Modified the USNJrnl collection argument to default to disabled collection.
* Improved SFTP handling to collect to a local zip file and attempt the
  upload three times, with a 30 second delay between attempts.
* Semantic changes to packaging and build scripts to avoid alias use.
* Added packaging script check to see if packaging tool was local before
  re-downloading.
* Updated argument usage information.
* Added tests to increase coverage of Arguments.cs
