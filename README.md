# unluac-d: Dockerized Luac decompiler 

Dockerized versions of [unluac](https://sourceforge.net/projects/unluac/) for decompiling luac files from wherigo containers regardless of the execution environment. 

Currently, dockerizes an old binary version `unluac_2015_06_13.jar` in two ways:
* `unluac-docker/` a dockerfile for creating 'standard' docker image that
  * reads input (luac file to decompile) from bind-mount and 
  * prints results to STDOUT
* `unluac-docker-faas/` a dockerfile (based on unloac-docker) for creating "function-as-a-service" docker image where unluac is wrapped with [OpenFaas](https://github.com/openfaas/faas)'s [function watchdog](https://github.com/openfaas/faas/tree/master/watchdog) to 
  * read input (luac file to decompile) from HTTP POST request
  * send results to HTTP POST response

The purpose is to make it easy to decompile luac files extracted from wherigo containers regardless of the execution environment.

## Usage
### unluac-docker: 

#### Build docker image
  
   `cd unluac-docker && docker build -t mrummuka/unluac-docker .`

#### Run docker container to decompile luac

   `docker run --rm -v /path/to/luacdir/:/data mrummuka/unluac-docker:latest`

**Note: unluac-docker expects to find `cartridge.luac` in `/path/to/luacdir/`**

### unluac-docker-faas: 
#### Build docker image
  
  `cd unluac-docker-faas && docker build -t mrummuka/unluac-docker-faas .`
  
#### Start docker container

  `docker run --rm -p 8080:8080 mrummuka/unluac-docker-faas:latest`

#### Decompile using unluac-docker-faas
    `curl -XPOST --data-binary @cartridge.luac localhost:8080 -o output.file`

### See also
 *  [Unluac](https://sourceforge.net/projects/unluac/)
 *  [openfaas](https://github.com/openfaas/faas)
 *  [function watchdog](https://github.com/openfaas/faas/tree/master/watchdog)

Licence
-------
* MIT
  * Unluac: unluac-docker/unluac_licence.txt
  * fwatchdog: unluac-docker-faas/openfaas_licence.txt

Sources
-------
[1] https://sourceforge.net/projects/unluac

[2] https://github.com/openfaas/faas/tree/master/watchdog