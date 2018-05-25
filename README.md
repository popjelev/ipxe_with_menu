# Requirements

## Download
Go to https://ipxe.org/download and check for the repository URL, in case it's different from the one in the example.

## In case you're getting a boot loop
Please read "Breaking the loop with an embedded script" section:
https://ipxe.org/howto/chainloading

## Dependencies
Please check dependencies on https://ipxe.org/download at Source section.
You will need to have at least the following packages installed in order to build iPXE:
- gcc (version 3 or later)
- binutils (version 2.18 or later)
- make
- perl
- liblzma or xz header files
- mtools
- mkisofs (needed only for building .iso images)
- syslinux (for isolinux, needed only for building .iso images)

## Bootstrapping menu sources
I've used this examples to simplify the booting with menu process:
https://gist.github.com/robinsmidsrod/2234639

# Deploying

## Clone the repository
```
git clone git://git.ipxe.org/ipxe.git
```

## Compile
```
cd ipxe/src
make bin/undionly.kpxe EMBED=boot.ipxe
```

## Upload
Copy all the files in TFTP server boot/ folder.

## Setup DHCP server
You need to add `Next Server` to be your `TFTP IP Address`. You'll also need to set `Boot File Name` to be `boot/undionly.kpxe`.

# Notes
File `undionly.ipxe` is loaded from IP Address assigned in your `Next Server`.
