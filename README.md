# SRE-AGENT Plugins
My solution to the challenge of cross compiling Go code with embedded C/C++ snippets (i.e. CGO_ENABLED=1) is based on the concept of lightweight Linux containers. All the necessary Go tool-chains, C cross compilers and platform headers/libraries have been assembled into a single Docker container, which can then be called as if a single command to compile a Go package to various platforms and architectures.

Although you could build the container manually, it is available as an automatic trusted build from Docker's container registry (not insignificant in size):
```
docker pull karalabe/xgo-latest
```
To prevent having to remember a potentially complex Docker command every time, a lightweight Go wrapper was written on top of it.
```
go get github.com/karalabe/xgo
```
Simply specify the import path you want to build, and xgo will do the rest:
```
xgo github.com/gus-maurizio/sre-agent-plugins
```

