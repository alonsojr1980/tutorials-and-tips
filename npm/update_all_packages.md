### Update all packages
https://www.npmjs.org/package/npm-check-updates <br>
```
$ npm install -g npm-check-updates
```
#### Basic usage:
```
$ ncu -u
$ npm install
```
#### Update packages to major versions:
```
$ ncu -u -semverLevel major
$ npm install
```
> Beware of possible breaking changes!

#### Update packages to minor verions:
```
$ ncu -u -semverLevel minor
$ npm install
```

#### Help
```
Usage: ncu [options] [filter]

[filter] is a list or regex of package names to check (all others will be ignored).

Options:
  --dep <dep>                  check only a specific section(s) of dependencies: prod|dev|peer|optional|bundle (comma-delimited)
  -e, --error-level <n>        set the error-level. 1: exits with error code 0 if no errors occur. 2: exits with error code 0 if no packages need updating (useful for continuous integration). Default is 1. (default: 1)
  -f, --filter <matches>       include only package names matching the given string, comma-delimited list, or regex
  -g, --global                 check global packages instead of in the current project
  -i, --interactive            Enable interactive prompts for each dependency
  -j, --jsonAll                output new package file instead of human-readable message
  --jsonUpgraded               output upgraded dependencies in json
  -l, --loglevel <n>           what level of logs to report: silent, error, minimal, warn, info, verbose, silly (default: warn) (default: "warn")
  -m, --minimal                do not upgrade newer versions that are already satisfied by the version range according to semver
  -n, --newest                 find the newest versions available instead of the latest stable versions
  -p, --packageManager <name>  npm (default) or bower (default: "npm")
  --packageData                include stringified package file (use stdin instead)
  --packageFile <filename>     package file location (default: ./package.json)
  --packageFileDir             use same directory as packageFile to compare against installed modules. See #201.
  --pre <n>                    Include -alpha, -beta, -rc. Default: 0. Default with --newest and --greatest: 1
  -r, --registry <url>         specify third-party npm registry
  --configFilePath <path>      rc config file path (default: ./)
  --configFileName <path>      rc config file name (default: .ncurc.{json,yml,js})
  -s, --silent                 don't output anything (--loglevel silent)
  -t, --greatest               find the highest versions available instead of the latest stable versions
  --timeout <ms>               a global timeout in ms
  -u, --upgrade                overwrite package file
  -x, --reject <matches>       exclude packages matching the given string, comma-delimited list, or regex
  --semverLevel <level>        find the highest version within "major" or "minor"
  --removeRange                remove version ranges from the final package version
  -v, --version                3.1.9
  -V                           
  -h, --help                   output usage information
```
