# Midea Lua protocol references

This repository contains Lua protocol scripts for Midea M-Smart appliances.
They document device-specific message handling and serve as references for
the Python implementations in [midea-local](https://github.com/midea-lan/midea-local).

## Layout

Scripts are grouped into folders by appliance type. For example, `ac/` contains
air-conditioner scripts and `a1/` contains dehumidifier scripts. Folder names
follow the device-type convention used by midea-local: lowercase hexadecimal,
with an `x` prefix for types below `0xA0` when needed (for example, `x13/`).

File names generally preserve the protocol or model identifiers and version
information available in the source. Naming details can vary between scripts.

## Use in midea-local

The Python package implements device communication and message parsing in
Python. These Lua files are protocol references for understanding and
maintaining those implementations; they are not Python modules.

When changing a parser in midea-local, use the corresponding script when one is
available and add or update regression tests in that project. If no Lua
reference exists, document the evidence used for the parser in the Python
source.

## Contributing

To contribute a Lua file or report an unsupported device, see
[CONTRIBUTING.md](./CONTRIBUTING.md).
