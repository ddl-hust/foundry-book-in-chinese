# forge update

更新一个或多个依赖项

```bash
$ forge update --help
Usage: forge update [OPTIONS] [DEPENDENCIES]...

Arguments:
  [DEPENDENCIES]...
          The dependencies you want to update

Options:
      --root <PATH>
          The project's root path.
          
          By default root of the Git repository, if in one, or the current working directory.

  -f, --force
          Override the up-to-date check

  -r, --recursive
          Recursively update submodules

  -h, --help
          Print help (see a summary with '-h')
```