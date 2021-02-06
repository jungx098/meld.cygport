# MELD Cygport

## Requirements for cygport development

- `git`
- `intltool`
- `xinit`
- `python3-gi`
- `girepository-Gtk3.0`
- `girepository-GtkSource3.0`

## Build

```
$ cygport meld.cygport download
$ cygport meld.cygport all
```

## Install

```
$ tar -C / -xvf ./meld-3.20.2-1.noarch/dist/meld/meld-3.20.2-1.tar.xz
```

## Uninstall

```
$ tar -tf ./meld-3.20.2-1.noarch/dist/meld/meld-3.20.2-1.tar.xz | sort -r | xargs -I {} echo /{} | while read file; do if [ -d "$file" ]; then rmdir "$file"; else rm -f "$file"; fi; done
```

## Troubleshooting

### No module named 'gi'

Install `python3-gi`

#### Error example

```
$ meld
Cannot import: GTK+
No module named 'gi'
```
