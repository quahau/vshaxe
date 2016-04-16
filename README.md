# Haxe for VS Code

This is an extension for [Visual Studio Code](https://code.visualstudio.com) that adds support for [Haxe](http://haxe.org/) language,
leveraging [Haxe Language Server](https://github.com/nadako/haxe-languageserver).

**Status**: just like the server, the extension is very much work in progress.
For general usage, see Jeff Ward's [vscode-haxe](https://github.com/jcward/vscode-haxe) extension as it's more mature at the moment.

## Hacking

1. Clone this repo to `~/.vscode/extensions`.
2. Init and update `server` submodule.
3. Do `npm install` (to install `vscode-languageclient` module required to connect to the language server).
4. Do `haxe build.hxml` (that will build both client and server)
5. Right now, by default, extension looks for the `build.hxml` file in the workspace root and uses that file
for completion. So it should only contain arguments that are used for completion (i.e. no --each/--next/-cmd/etc.)
6. You can specify custom hxml file to use with `"haxe.buildFile"` setting.

## Build task

Example `tasks.json` file (the problem matcher is submitted to https://github.com/Microsoft/vscode/pull/5370)
```json
{
    "version": "0.1.0",
    "command": "haxe",
    "args": ["build.hxml"],
    "problemMatcher": {
        "owner": "haxe",
        "pattern": {
            "regexp": "^(.+):(\\d+): (?:lines \\d+-(\\d+)|character(?:s (\\d+)-| )(\\d+)) : (?:(Warning) : )?(.*)$",
            "file": 1,
            "line": 2,
            "endLine": 3,
            "column": 4,
            "endColumn": 5,
            "severity": 6,
            "message": 7
        }
    }
}
```

## Type hint
![Type hint](images/type.png)

## Goto definition
![Goto definition](images/position.png)

## Completion
![Field completion](images/field.png)

## Peek definition
![Peek definition](images/peek.png)