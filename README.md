# Oracle compiler for Atom

Uses the [atom-build](https://atom.io/packages/build) package to execute Oracle compilations in the Atom editor.

This package requires [atom-build](https://atom.io/packages/build) to be installed.

## Installation

Currently, this package has not been published the Atoms package repository. To install, you should add it to your package directory. After installation, you should be able to find it listed under community packages in the relevant settings page.

![](https://cloud.githubusercontent.com/assets/1747643/11413140/e4b75b26-9439-11e5-86f5-7bb7dcb19b39.png)

Once installed, you will want to access the settings and set the relevant path for your SQL interpreter. That will be either SQLcl or SQL*Plus. For me, I have `sqlplus` in my `path` - so no change is necessary. If I wanted to point it to the binary for `SQLcl`, which isn't in my `path`, I would set the configuration to `/opt/sqlcl/bin/sql`.

![](https://cloud.githubusercontent.com/assets/1747643/11413201/79fcaa10-943a-11e5-881f-1715ef163e29.png)

## Usage instructions

In your project root directory, add a JSON file named `.atom-build-oracle.json`, where you can define build targets for your project. This contents of the file should look like:

```json
[
    {
        "targetName" : "hr: dev",
        "host" : "example.com",
        "sid" : "xe",
        "port" : 1521,
        "user" : "hr",
        "password" : "hr"
    }
]
```

Where you can specify any number of build targets.

Since this file contains sensitive information (password) you will likely also want to add an entry to your `.gitignore` file so this is not published.

```conf
.atom-build-oracle.json
```

It's worth noting, that to get the build system to recognise the above configuration, you will need to reload atom (only the first time). This can be done in the menu `View->Reload` or with the keyboard shortcut `ctrl+alt+r`.
