# Locales support for musl
Locale program for musl libc

This is ```/usr/bin/locale```, which works on musl libc (with limitations in musl itself).
To install, use ```cmake . && make && make install``` on musl-capable distro.
English and Russian included, also .pot file.

```bash
locale -a

C
C.UTF-8
en_GB.UTF-8
ch_DE.UTF-8
fr_FR.UTF-8
es_ES.UTF-8
ru_RU.UTF-8
de_CH.UTF-8
es_CO.UTF-8
en_US.UTF-8
de_DE.UTF-8
fr_FR.UTF-8
```

## Build requirements:
 - musl (with developer tools)
 - gettext (with libintl and developer tools)
 - С compiler (gcc or clang recommended)
 - CMake
 - CMake backend provider (make or ninja)

## For alpine -> Dockerfile installation example

Taken from https://github.com/gliderlabs/docker-alpine/issues/144

```dockerfile
ENV MUSL_LOCPATH=/usr/local/share/i18n/locales/musl
RUN apk add --update git cmake make musl-dev gcc gettext-dev libintl
RUN cd /tmp && git clone https://github.com/jpmzx/musl-locales.git
RUN cd /tmp/musl-locales && cmake . && make && make install
```

## Test translations after build - Bash

```bash
date
// Mon Aug 26 10:23:47 -05 2019
LANG=es_CO.UTF-8 date
// Lun Ago 26 10:24:08 -05 2019
```

## License

 - All translations and scripts uses [MIT](LICENSE.MIT)
 - Source files for `/usr/bin/locale` uses [LGPL](LICENSE)
