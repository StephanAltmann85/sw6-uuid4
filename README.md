# SW6 UUID4

This project is based on https://github.com/gpakosz/uuid4. This fork simply removes the dashes between the chunks to provide sw6 compatible ids.

## Compiling for Linux or Mac

There is a GNU Make 3.81 `MakeFile` in the `_gnu-make/` folder:

    $ make -j -C _gnu-make/