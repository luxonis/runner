
# GitHub Actions Runner - Luxonis Fork

The runner is the application that runs a job from a GitHub Actions workflow. This forks primary intention is to provide extra security against running untrusted code from PRs on self-hosted runners until the issue is resolved by Github with proper policies.

Auto updating is disabled.

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

Similar to building, packaging can be performed using:
```
./dev.sh package Release [runtime]
```
For `runtime` see above list under [Building](#Building) section

Created packages can be found in `_package` folder