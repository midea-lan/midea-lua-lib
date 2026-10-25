# Contributing Lua files

Midea Lua files describe parts of an appliance's protocol and capabilities.
They help investigate unsupported devices and features and provide protocol
references for the Python implementations in
[midea-local](https://github.com/midea-lan/midea-local).

## Download a Lua file

The `midea-local` command-line interface can download the Lua file and its
companion plugin from Midea's cloud service.

Install `midea-local` if it is not already available:

```bash
pip install midea-local
```

See the available options for your installed version:

```bash
python3 -m midealocal.cli download -h
```

You can identify a device by its IP address, if it is powered on and reachable:

```bash
python3 -m midealocal.cli download --host 192.168.1.100
```

Or download by serial number (S/N), even when the device is not currently
reachable:

```bash
python3 -m midealocal.cli download --device-sn <serial-number>
```

The CLI can determine the device type from a standard 32-character hexadecimal
S/N. If it cannot, pass the type explicitly as hexadecimal without a `0x`
prefix:

```bash
python3 -m midealocal.cli download --device-sn <serial-number> --device-type ac
```

Downloading requires a Midea cloud account. The CLI may use its preset account
when no credentials are supplied; otherwise, pass credentials with the command
or save them locally with `midea-local.json` using the `save` command. Supported
cloud names include `美的美居`, `SmartHome`, `Midea Air`, `NetHome Plus`, and
`Ariston Clima`; use the cloud for the app where the device is registered. Keep
account credentials private: do not include them in issues, pull requests, or
uploaded files.

On success, the CLI reports the paths of the downloaded Lua and plugin files.
The filenames are supplied by Midea's cloud service, so use the paths in the
CLI output rather than assuming a filename. Add `--debug` to a CLI command for
verbose troubleshooting logs.

## Report an unsupported device or feature

Open a new device-support request as an issue in the
[midea-local repository](https://github.com/midea-lan/midea-local/issues),
not in this Lua submodule.

If you can download the Lua file, attach it when reporting the unsupported
device or feature. Otherwise, provide as much of the following as possible:

- Device model and type
- Device ID
- Serial number (S/N)
- Cloud/server region
- Firmware version
- Other relevant information shown by the Midea app

The S/N can help retrieve a device's Lua definition, but it uniquely identifies
a device. Do not post it publicly unless you are comfortable sharing it; use a
private channel when appropriate. Do not include cloud passwords or other
account credentials in a report.

Device details are usually available in the Midea app under **Settings**,
**Device Information**, or **About**. When sharing details, a template is:

```text
Model: <model>
Device type: <type>
Device ID: <device-id>
S/N: <serial-number>
Firmware: <firmware-version>
Region: <cloud/server-region>
```

For more detail, see the project's
[Providing a Lua File wiki page](https://github.com/midea-lan/midea-local/wiki/Providing-a-Lua-File).
