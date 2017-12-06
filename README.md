# Clarity Hub JavaScript Style Guide

*Eslints for the Clarity Hub world.*

In order to use any of these linters, you will need to use yarn, and add `git+ssh://gitlab.com:clairvoyance/eslint-config-claire.git`. Since this repo is protected, you will need to to authenticate to clone it.

## CI Usage

For a CI, you will need an `SSH_SERVER_HOSTKEY` and an `SSH_PRIVATE_KEY`. Then you will want to add the following script as well:

```bash
#!/bin/bash

# Run ssh-agent (inside the build environment)
eval $(ssh-agent -s)

mkdir -p ~/.ssh

echo "
Host gitlab.com
        PubkeyAcceptedKeyTypes +ssh-rsa
        HostName gitlab.com
        IdentityFile ~/.ssh/gitlab
        User git
" >> ~/.ssh/config

echo "$SSH_SERVER_HOSTKEY" >> ~/.ssh/known_hosts

echo "$SSH_PRIVATE_KEY" > ~/.ssh/gitlab
chmod 400 ~/.ssh/gitlab

# Add the SSH key stored in SSH_PRIVATE_KEY variable to the agent store
ssh-add ~/.ssh/gitlab
```

Check other repos (like the website repo) for the `SSH_PRIVATE_KEY`.

## Available Linters

1. [node-mocha](#node-mocha)
2. [node](#node)
3. [preact](#preact)
4. [react](#react) – DEPRECATED

### node-mocha

Usage:

```sh
yarn add --dev git+ssh://gitlab.com:clairvoyance/eslint-config-claire.git
```

```json
{
  "extends": ["claire/node-mocha"]
}
```

### node

Usage:

```sh
yarn add --dev git+ssh://gitlab.com:clairvoyance/eslint-config-claire.git eslint-config-airbnb
```

```json
{
  "extends": ["claire/node"]
}
```

### preact

Usage:

```sh
yarn add --dev git+ssh://gitlab.com:clairvoyance/eslint-config-claire.git eslint-config-standard-preact eslint-config-standard eslint-plugin-import eslint-plugin-node eslint-plugin-promise eslint-plugin-standard
```

```json
{
  "extends": ["claire/preact"]
}
```

### react

Usage:

```sh
yarn add --dev git+ssh://gitlab.com:clairvoyance/eslint-config-claire.git eslint-config-react-app
```

```json
{
  "extends": ["claire/react"]
}
```
