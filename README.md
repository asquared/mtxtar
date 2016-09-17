# mtxtar
Really simple wrapper scripts for tar backup to tape library / autoloader.

## Prerequisites
working `mtx` and `tar` commands.

## Installation
`install -m 755 mtxtar mtxtar_tapechange /usr/local/bin`

## Usage
Set environment variables: FIRST_TAPE to the first tape index you want to use 
for this archive, and LAST_TAPE to the last. Then use it like normal tar e.g:
`mtxtar -b 1024 -cvf /dev/st0 -C /path/to/your/data .` or
`mtxtar -b 1024 -xvf /dev/st0`. The wrapper takes care of changing tapes and
aborting the `tar` process if a tape change should fail.

## Caveats
This script has no awareness of when the drive needs to be cleaned, and will
not request that the cleaning tape be loaded when that time comes. I'm not
really sure if that's necessary or if the autoloader will just do it.

This script is really, really dumb. For general-purpose backup you'd be well
advised to look elsewhere for a more complete system. If you know what you
want and know what you're doing, then this may be the tool for you.

## License
MIT, see LICENSE file.
