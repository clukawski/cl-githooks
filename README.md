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

This hook will make various checks to your file changes before you commit.
You'll want to edit the hookconfig dictionary in main() to the tools/language
you are using.

Currently the linter/unit test checks only support one language/tool each,
will add support for multiple passes per check later.

* warnfiles:
	* list of files you want warnings when committing changes to

* linter: Linter settings
	* extension: file extension for the linter to use
	* executable: linter executable
	* arguments: arguments to pass to the linter
* testing: Unit testing settings
	* executable: unit test tool executable
	* arguments: arguments to pass to the tool
    * testoutput: show unit test tool output
    	* set to True or False 
* checks: List of enabled checks
    * lint_files: use the linter check
    * warn_files: use the file warning check
    * test_files: use unit test check

```python
    hookconfig = {
        'warnfiles': [
            'src/test.php',
        ],
        'linter': {
            'executable': 'php',
            'extension': '.php',
            'arguments': [
                '-l'
            ]
        },
        'testing': {
            'executable': 'phpunit',
            'arguments': [
                '-v'
            ],
            'testoutput': True
        },
        'checks': [
            'lint_files',
            'warn_files',
            'test_files'
        ]
    }

```