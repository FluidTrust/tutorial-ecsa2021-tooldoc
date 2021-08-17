# Tool Documentation for Tutorial at ECSA 2021

![https://github.com/FluidTrust/tutorial-ecsa2021-tooldoc/actions/workflows/publish-documentation.yml?query=branch%3Amain++](https://github.com/FluidTrust/tutorial-ecsa2021-tooldoc/actions/workflows/publish-documentation.yml/badge.svg?branch=main)

This repository contains the documentation for the tooling to be used at the tutorial at ECSA 2021. The most recent version is always available on [Github Pages](https://fluidtrust.github.io/tutorial-ecsa2021-tooldoc/).

## How to build locally
The simplest way is to use the docker image provided in this repository. Do the following steps:
* build the builder image (`docker build -t build-environment .`)
* run the build within a docker container (`docker run --rm -v $PWD:/docs build-environment make clean html`)

The build output will be located in `build/html`.
