# github-action-mypy
A Github Action that runs a [mypy](https://mypy.readthedocs.io/en/stable/) check on a pull request and leaves a comment on your pull request.

## Example

#### Create `.github/workflows/mypy.yml`:
```
on: [pull_request]
name: Python mypy Check
jobs:
  mypy:
    name: mypy
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: mypy
      uses: konciergeMD/github-action-mypy@main
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        MYPY_OPTS: "--config=./.github/workflows/mypy.ini"  # additional mypy options
        #MYPY_CODE_DIR: "."  # what directory to check, defaults to "."
        #PRECOMMAND_MESSAGE: You have style errors. See them below.
```

#### Create `./.github/workflows/mypy.ini`

TODO: Create an example config file:
```
```
Please find additional information in the official [documentation](https://mypy.readthedocs.io/en/stable/command_line.html#config-file-flag)

#### Additional options
* `PRECOMMAND_MESSAGE` - if you set it, it will print before
the code errors. For example, this is helpful if you want to print a message to refer the user
to any tools you have for managing style errors.
* `MYPY_OPTS` - in case you don't want to use the `mypy` configuration file, update this variable and set additional `mypy` options, like `--ignore=E501,W303`, etc.
* `MYPY_CODE_DIR` - what directory to check, defaults to the root of the repository `.`
