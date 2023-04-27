# MELD Cygport

-------------------------------------------------------------------------------
## Requirements for cygport development

- `cygport`
- `git`
- `intltool`
- `xinit`
- `python3`
- `python3-cairo`
- `python3-gi`
- `diffutils`
- `patch`
- `girepository-Gtk3.0`
- `girepository-GtkSource3.0`

-------------------------------------------------------------------------------
## Patch Generate

If cygwin specific changes are required, generate patches and update `PATCH_URI` in `meld.cygport`

### Patch Generate Example

```sh
$ diff -Naur ./origsrc ./src > ../meld-3.20.4-1.patch
```

### Manual Patch Apply Example

Manually apply patches to source tree for verification

```sh
patch -p3 < ../meld-3.20.4-1.patch
```

-------------------------------------------------------------------------------
## Build

```sh
$ cygport meld.cygport download
$ cygport meld.cygport all
```

### Note

`cygport` direct package installation NOT available

> Unfortunately, there is no tool for directly installing package files, at the moment.
> - http://www.cygwin.com/packaging-contributors-guide.html

-------------------------------------------------------------------------------
## Manual Install

Extract the distribution package to `/`

```sh
$ tar -C / -xvf ./meld-3.20.4-1.noarch/dist/meld/meld-3.20.4-1.tar.xz
```

Run post install shell script (icon cache refresh, or run `gtk-update-icon-cache`)

```sh
$ /etc/postinstall/meld.sh
```

-------------------------------------------------------------------------------
## Manual Uninstall

```sh
$ tar -tf ./meld-3.20.4-1.noarch/dist/meld/meld-3.20.4-1.tar.xz | sort -r | xargs -I {} echo /{} | while read file; do if [ -d "$file" ]; then rmdir "$file"; else rm -f "$file"; fi; done
```

-------------------------------------------------------------------------------
## Troubleshooting

### No module named 'gi'

Install `python3-gi`

#### Error example

```sh
$ meld
Cannot import: GTK+
No module named 'gi'
```

-------------------------------------------------------------------------------
## Links

### Cygwin Package Contributor's Guide
http://www.cygwin.com/packaging-contributors-guide.html
