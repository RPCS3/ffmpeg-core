## FFmpeg builtins

This repository contains the ffmpeg builtins for RPCS3 and the CI to build them using vcpkg and github action.

The Windows version is built using clang-cl, this is done so that inline assembly optimisations (which are not supported by MSVC) can be enabled.

How to update:
- checkout https://github.com/microsoft/vcpkg to any directory (you only need it to create a ffmpeg.patch)
- reset the vcpkg branch/HEAD to the latest tag
- replace vcpkg commit/tag in .github/workflows/build.yml with the latest tag
- manually apply the changes found in the current ffmpeg.patch as well as any new changes to the vcpkg/ports/ffmpeg/portfile.cmake
- create new patch
	git diff > ffmpeg.patch
- replace our ffmpeg.patch with the new ffmpeg.patch
- push the two files changes to master (ffmpeg.patch and build.yml)
- wait for and download the new release in github actions
- replace new lib and include contents in our submodule