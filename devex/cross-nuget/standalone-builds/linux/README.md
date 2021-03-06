# Standalone Linux Build

To create the bits required for the Cross-Platform package on Linux:

1. Build OP-TEE using the `build-optee.sh` script, or use an existing OP-TEE build.
2. Build the bits generated by the SDK using the `runner.sh` script.
3. Package the bits, including the Windows bits, using the `pack.sh` script.

Note that the second step is dependent on the first step, and will build in the same directory. For more information, please refer to the [cross-plat documentation](https://github.com/openenclave/openenclave/tree/master/devex/cross-nuget).

The following environment variables are required by one or both of the scripts above:

`OE_SDK_PATH`:      Path to your local Open Enclave SDK repository
`BUILD_PATH`:       Path of the build bits; this should include the Windows bits
`OPTEE_BUILD_PATH`: Path of the OP-TEE bits
`PACK_PATH`:        Path where the bits will be packaged to
`OS_CODENAME`:      Ubuntu OS (bionic for 18.04, xenial for 16.04)

Prior to running the scripts, set the environment variables by:

`export <VAR>=<VAR VALUE>`

To simplify the process, keep the variables in a source file as such:

`sourcefile`
```
OE_SDK_PATH=<path>
...
```

And executing the commands as such:

`eval $(cat <sourcefile>) bash <script to run, ie., build-optee.sh, runner.sh, or pack.sh>`
