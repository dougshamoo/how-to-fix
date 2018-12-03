Upon starting a terminal session in vs code...

```
nvm is not compatible with the npm config "prefix" option...
```

You probably have a system and/or brew install of node that vs code is trying to use. helpful link:

https://github.com/Microsoft/vscode-docs/blob/master/docs/editor/integrated-terminal.md#why-is-nvm-complaining-about-a-prefix-option-when-the-integrated-terminal-is-launched

The gist of this solution is to uninstall all node installations that are not managed by nvm.

Also of note, if you used brew to install yarn with `brew install yarn`, it will have also installed node as a dependency. vs code picks up on this installation before finding nvm node installations apparently. In this case, the solution is to do the following:

```sh
brew uninstall yarn
brew uninstall node
brew install yarn --without-node
```