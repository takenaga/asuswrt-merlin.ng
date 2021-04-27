This document hopes to help folks with non-Windows environment to build Merlin image.
Information was gathered from https://github.com/RMerl/asuswrt-merlin.ng/wiki/Compiling-under-WSL2.


I've tested this workflow on M1 MacBookAir - please report issue if it doesn't work for you.

# Create docker environment
Download Dockerfile to your host (i.e. Mac), then run below command to build docker environment.
```
docker build --tag merlin-dev ./
```

# Enter docker environment
```
docker run -it --platform linux/amd64 merlin-dev bash
```

# Build image
Wiki suggests rsync for cleanup, but you can actually use below command to clean up
```
git clean -fdx
```

Anyhow, change directory
```
cd ~/asuswrt-merlin.ng/
```

Then follow wiki page
- Search for "Your setup is now ready for compiling"
- Replace ~/amng-build/ with ~/asuswrt-merlin.ng/
- https://github.com/RMerl/asuswrt-merlin.ng/wiki/Compile-Firmware-from-source

