# Notify Crystal Bindings

This is a fork of [hugopl/gtk4.cr](https://github.com/hugopl/gtk4.cr), but for [Notify](https://lazka.github.io/pgi-docs/#Notify-0.7). Please see that other repo for details or read on below.

In fact, this very repository only consists out of four lines of code because most of the development happens in the [binding generator repository](https://github.com/hugopl/gi-crystal), not here.

There's also the more popular and more battle-tested [jhass/crystal-gobject](https://github.com/jhass/crystal-gobject) for GTK3. Both bindings are not compatible, but migrating is not hard. I made this very alternative because when I used the other one, there were rare different rare crashes which I couldn't resolve.

If you need GTK3, you can use https://github.com/phil294/gtk3.cr.

## API docs

Current documentation is far from being good, but is better (not much) than nothing.

To generate the documentation clone this repository then do:

```
$ make doc
```

The documentation will be found at `docs/index.html`. (NOT TESTED)


## Compile time dependencies

You need the GTK libraries and their GObjectIntrospection files.

- Archlinux: `pacman -S gtk4 gobject-introspection`
- Ubuntu: `apt-get install libgtk-4-1 libgirepository1.0-dev gobject-introspection gir1.2-gtk-4.0`
- macOS: `brew install gobject-introspection gtk4`

Be welcome to create a PR updating this readme once you know what packages are needed by your distro to run the
examples.

## Runtime dependencies

Just the Notify libraries are needed at runtime, i.e. not the `gobject-introspection` library and files.

## Installation

1. Add the dependency to your `shard.yml`:

   ```yaml
   dependencies:
     notify:
       github: phil294/notify.cr
   ```

2. Run `shards install`

3. Run `bin/gi-crystal`

## Usage

Example usage:
```crystal
require "notify"
notify_status = Notify.init("myapp_name")
n = Notify.Notification.new(title, text, file_path_to_icon)
n.show()
```
For more details, check the generated source after install in `./lib/gi-crystal/src/auto/notify`

## Contributing

1. Fork it (<https://github.com/phil294/notify.cr/fork>)
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request

## Contributors

- [Philip Waritschlager](https://github.com/phil294) - creator and maintainer
