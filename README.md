# unluac-docker: Dockerized luac decompiler 

This is a dockerized version of an old (`unluac_2015_06_13.jar`) version of [unluac](https://sourceforge.net/projects/unluac/).

The purpose is to make it easy to complie luac files extracted from wherigo containers regardless of execution environment.

## Usage
### Build docker image locally
`docker build -t mrummuka/unluac-docker .`

### Run dockerized
`docker run --rm -v /path/to/luacdir/:/data mrummuka/unluac-docker:latest`

.. decompiles cartridge.luac to STDOUT 


**Note: unluac-docker expects to find cartridge.luac from /path/to/luacdir/**


### See also
 *  [GWCD for unpacking/decompiling wigo container](https://github.com/mrummuka/gwcd)

Licence
-------
See unluac_licence.txt

Sources
-------
[1] https://sourceforge.net/projects/unluac/
