
# GitHub Actions Runner - Luxonis Fork

The runner is the application that runs a job from a GitHub Actions workflow. This forks primary intention is to provide extra security against running untrusted code from PRs on self-hosted runners until the issue is resolved by Github with proper policies.

## Changes

 - Auto updating is disabled.
 - PR jobs disabled by default.

Pull request behaviour can be modified by adding the following to  the `.runner` config file:

```
  "pullRequestSecurity": {}
```

This enables jobs executed by PRs from Contributors

It is also possible to explicitly list users that are allowed to run
jobs on this worker:

```
  "pullRequestSecurity": {
    "allowedAuthors": ["ashb"]
  }
```

Or to _only_ allow the given users, but not all contributors:

```
  "pullRequestSecurity": {
    "allowContributors": false,
    "allowedAuthors": ["ashb"]
  }
```

## Building

To build the application use `dev.sh` or `dev.cmd` scripts in `src/` folder:
```
./dev.sh build [runtime]
```
Where `runtime` can be one of the following:
  - linux-arm64
  - linux-arm
  - osx-x64
  - win-x64
  
## Packaging

Similar to building, packaging can be performed using (make sure to build first):
```
./dev.sh package Release [runtime]
```
For `runtime` see above list under [Building](#Building) section

Created packages can be found in `_package` folder

## Releasing

To track the upstream (actions/runner) releases, fetch the latest release branch under `releases/m?` and merge in `pr-security-branch` branch. Bump patch version in `releaseVersion`, `runnerversion` and create a tag.

After pushing to remote, everything will be done using CI/CD. You can find packages under `https://github.com/luxonis/runner/releases`