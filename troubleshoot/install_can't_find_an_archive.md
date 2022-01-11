# Error
``text
E: The package hl1440lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
``

#### To remove package

```bash
sudo dpkg --remove --force-all hl1440lpr
```

## If that fails:

```bash
sudo rm -i /var/lib/dpkg/info/hl1440lpr.*
sudo dpkg --remove --force-remove-reinstreq hl1440lpr
```

### Confirm Apt is fixed. The following command should return no errors

```bash
sudo apt-get update
```
