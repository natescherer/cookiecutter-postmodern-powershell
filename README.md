# cookiecutter-postmodern-powershell: A Modern Template for PowerShell Module Development on GitHub

[![All Contributors](https://img.shields.io/github/all-contributors/natescherer/cookiecutter-postmodern-powershell?color=ee8449&style=flat-square)](#contributors)

`cookiecutter-powershell-module` is a [Cookiecutter](https://github.com/cookiecutter/cookiecutter) template for modern, open-source PowerShell module development using GitHub Actions CI/CD.

Included features:


- Useful project support files
  - `.gitignore`, set to ignore macOS `.DS_Store` files
  - `CODE_OF_CONDUCT.md`, derived from [The Contributor Covenant](https://www.contributor-covenant.org/), with intructions to report issues via [GitHub private vulnerability reporting](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability)
  - `CONTRIBUTING.md`, designed for novices to make their first contribution
  - `LICENSE`, a copy of the [MIT License](https://choosealicense.com/licenses/mit/)
  - `README.md`, designed for novices to installing PowerShell modules
- Automatic publishing to [Cloudsmith](https://cloudsmith.com/) for development versions and to the [PowerShell Gallery](https://www.powershellgallery.com/) for stable versions
- Testing and code coverage evaluation via [Pester](https://pester.dev/), with publishing of test results to GitHub Pages and, optionally, [Codecov](https://about.codecov.io/)
<!-- - Linting via [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) -->
- Generation of help docs (in Markdown and HTML) from [Comment-Based Help](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- Module structure built around one function per file, with support for both private and public functions
- Simple changelog creation and upkeep in [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format
- Automatic [SemVer](https://semver.org/) version number handling via [GitVersion](https://gitversion.net/)
- Simple contributor management and crediting via [All Contributors](https://allcontributors.org/)
- Automatic updating of GitHub Actions workflows via [Dependabot](https://docs.github.com/en/code-security/getting-started/dependabot-quickstart-guide)

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

## Feedback, Contributions, and Reports

If you have questions, comments, etc, please enter a GitHub Issue with the `question` tag.

For bugs, please enter a GitHub Issue with the `bug` tag.

For security issues, please see [SECURITY.md](SECURITY.md)

If you would like to make a contribution, please see [CONTRIBUTING.md](CONTRIBUTING.md).

## Building

Building is unnecessary, per se. The provided build YAML generates documentation files and metadata, then does the actual releasing and publishing. If modifying locally, you can simply use the updated .psd1/.psm1 files without running a build process.

## License

This project is licensed under The MIT License - see [LICENSE](LICENSE) for details.

## Contributors

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://allcontributors.org) specification.
Contributions of any kind are welcome!