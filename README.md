# scoop-senzingsdk

[Scoop](https://scoop.sh/) bucket for installing the [Senzing SDK](https://senzing.com/senzing-api/) on Windows.

## Usage

### Add the bucket

```pwsh
scoop bucket add senzingsdk https://github.com/Senzing/scoop-senzingsdk
```

### Install the Senzing SDK

```pwsh
scoop install senzingsdk/senzingsdk
```

During installation you will be prompted to accept the [Senzing EULA](https://senzing.com/software-license-agreement/).
To accept in advance (e.g. for automation), set one of:

```pwsh
# Option 1: environment variable
$env:I_ACCEPT_THE_SENZING_EULA = "yes"

# Option 2: scoop config
scoop config I_ACCEPT_THE_SENZING_EULA yes
```

### Update

```pwsh
scoop update senzingsdk
```

### Uninstall

```pwsh
scoop uninstall senzingsdk
```

### Remove the bucket

```pwsh
scoop bucket rm senzingsdk
```

## What gets installed

- `SENZING_DIR` environment variable is set to the Senzing engine runtime directory
- Senzing libraries are added to `PATH`

To verify:

```pwsh
echo $env:SENZING_DIR
```

## References

- [Senzing Quick Start guides](https://docs.senzing.com/quickstart/)
- [Senzing EULA](https://senzing.com/software-license-agreement/)
