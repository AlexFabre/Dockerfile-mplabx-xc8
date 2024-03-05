# MPLAB X - xc8

This Dockerfile provides a build environement for your MPLAB X - xc8 project.

It gives access to the following tools:

- xc8 in a specific version(*)
- MPLAB X ide in the most recent version.

**(*)Docker image tags are named according to the version of xc8 installed in the image.**

# Registry

This docker image is available on [Docker hub](https://hub.docker.com/r/alexfabre/mplabx-xc8)

# Example usage in a Github repo

Complete your `.github/workflows/build.yml` with:

```yaml
jobs:
  build:
    name: Build project
    runs-on: ubuntu-latest
    container: alexfabre/mplabx-xc8:2.46
    steps:
      - name: Download source
        uses: actions/checkout@v1

      - name: MPLAB Makefiles generation
        run: prjMakefilesGenerator.sh project_name.X
      
      - name: Build debug
        run: make -C project_name.X CONF=debug build
      
      - name: Build release
        run: make -C project_name.X CONF=release build
```
