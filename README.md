# some python git hooks

Note: These are a work in progress.

## Requirements

* python 2.7

## Current Hooks Available

* pre-commit

## Individual Installation

```sh
$ git clone https://github.com/clukawski/cl-githooks
$ cd cl-githooks
$ cp /path/to/{hookname} /path/to/project/.git/hooks/{hookname}
$ chmod +x /path/to/project/.git/hooks/{hookname}
```

## Hook Usage/Customization

### pre-commit:

You'll want to edit the dictionary in main()

* warnfiles: list of files you want git to stop/warn you from committing changes to (use --no-verify to override), maybe these files shouldn't change, or you need to take extra care with these.
* linter:
	* extension: file extension for the linter to use
	* executable: linter executable
	* arguments: arguments to pass to the linter 

```python
    hookconfig = {
        'warnfiles': [
            'src/test.php'
        ],
        'linter': {
            'extension': '.php',
            'executable': 'php',
            'arguments': [
                '-l'
            ]
        }
    }

```