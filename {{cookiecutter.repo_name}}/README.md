# {{cookiecutter.module_name}}

[![Tests Windows PowerShell](https://{{cookiecutter.github_username}}.github.io/{{cookiecutter.module_name}}/testreports/Windows_powershell/Windows_powershell_badge.svg)](https://{{cookiecutter.github_username}}.github.io/{{cookiecutter.module_name}}/testreports/Windows_powershell/Windows_powershell.html)
[![Tests Windows Pwsh](https://{{cookiecutter.github_username}}.github.io/{{cookiecutter.module_name}}/testreports/Windows_pwsh/Windows_pwsh_badge.svg)](https://{{cookiecutter.github_username}}.github.io/{{cookiecutter.module_name}}/testreports/Windows_pwsh/Windows_pwsh.html)
[![Tests Linux](https://{{cookiecutter.github_username}}.github.io/{{cookiecutter.module_name}}/testreports/Linux_pwsh/Linux_pwsh_badge.svg)](https://{{cookiecutter.github_username}}.github.io/{{cookiecutter.module_name}}/testreports/Linux_pwsh/Linux_pwsh.html)
[![Tests macOS](https://{{cookiecutter.github_username}}.github.io/{{cookiecutter.module_name}}/testreports/macOS_pwsh/macOS_pwsh_badge.svg)](https://{{cookiecutter.github_username}}.github.io/{{cookiecutter.module_name}}/testreports/macOS_pwsh/macOS_pwsh.html)
[![codecov](https://codecov.io/gh/{{cookiecutter.github_username}}/{{cookiecutter.module_name}}/branch/main/graph/badge.svg?token=rXSOfdrmo2)](https://codecov.io/gh/{{cookiecutter.github_username}}/{{cookiecutter.module_name}})
[![All Contributors](https://img.shields.io/github/all-contributors/{{cookiecutter.github_username}}/{{cookiecutter.module_name}}?color=ee8449&style=flat-square)](#contributors)

{{cookiecutter.short_description}}

## Features

The primary feature is automatic updating of changelogs at release time in a CI/CD workflow via Update-Changelog.

Other features include:

- Creating new changelog files via New-Changelog
- Adding data to changelog files via Add-ChangelogData
- Getting changelog contents (parsed into a PowerShell object) via Get-ChangelogData
- Converting changelogs into other formats via ConvertFrom-Changelog

## Getting Started

{{cookiecutter.module_name}} is designed to be cross-platform and fully compatible with Windows PowerShell 5.1 and PowerShell 7+ on Windows/Linux/macOS.

### Prerequisites

No prerequisites are required beyond having PowerShell installed.

### Installing

{{cookiecutter.module_name}} is listed in the PowerShell Gallery [here](https://www.powershellgallery.com/packages/{{cookiecutter.module_name}}), which means you can install on any internet-connected computer running PowerShell 5.1+ by running this command:

```PowerShell
Install-Module -Name {{cookiecutter.module_name}}
```

## Usage

### Examples

``` PowerShell
LinkPattern   = @{
    FirstRelease  = "https://github.com/testuser/testrepo/tree/v{CUR}"
    NormalRelease = "https://github.com/testuser/testrepo/compare/v{PREV}..v{CUR}"
    Unreleased    = "https://github.com/testuser/testrepo/compare/v{CUR}..HEAD"
}
Update-Changelog -ReleaseVersion 1.1.1 -LinkMode Automatic -LinkPattern $LinkPattern
```

- Does not generate output, but:
  - Takes all Unreleased changes in .\CHANGELOG.md and adds them to a new release tagged with ReleaseVersion and today's date.
  - Updates links according to LinkPattern.
  - Creates a new, blank Unreleased section.

``` PowerShell
New-Changelog
```

- Does not generate output, but creates a new changelog at .\CHANGELOG.md.

``` PowerShell
Add-ChangelogData -Type "Added" -Data "Spanish language translation"
```

- Does not generate output, but adds a new Added change into changelog at  .\CHANGELOG.md.

``` PowerShell
Get-ChangelogData
```

- Returns an object containing Header, Unreleased, Released, Footer, and LastVersion properties.

``` PowerShell
ConvertFrom-Changelog -Path .\CHANGELOG.md -Format Release -OutputPath docs\CHANGELOG.md
```

- Does not generate output, but creates a file at docs\CHANGELOG.md that is the same as the input with the Unreleased section removed.

### Documentation

For detailed documentation, [click here on GitHub](docs), see the docs folder in a release, or run Get-Help for the individual function in PowerShell.

## Questions/Comments

If you have questions, comments, etc, please enter a GitHub Issue with the "question" tag.

## Contributing/Bug Reporting

Contributions and bug reports are gladly accepted! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## Building

Building is unnecessary, per se. The provided build YAML generates documentation files and metadata, then does the actual releasing and publishing. If modifying locally, you can simply use the updated .psd1/.psm1 files without running a build process.

## Contributors

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://allcontributors.org) specification.
Contributions of any kind are welcome!

## License

This project is licensed under The MIT License - see [LICENSE](LICENSE) for details.

## Acknowledgements

[![Hosted By: Cloudsmith](https://img.shields.io/badge/OSS%20hosting%20by-cloudsmith-blue?logo=cloudsmith&style=flat-square)](https://cloudsmith.com)

Package repository hosting is graciously provided by Cloudsmith.
