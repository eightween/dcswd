# dcswd

Welcome to the unofficial DCS World Lua API documentation, (DCSWD) primarily designed
to document unknown globals, constants and functions written for
[plugins](https://dcswd.readthedocs.io/en/latest/lua.html).

**This is not a replacement** for
[BGDAM](https://forum.dcs.world/topic/97337-beginners-guide-to-dcs-world-aircraft-mods),
instead a continuation of [BGSC](https://bgsc.rtfd.io/) on a broader level. Information is
tailored around learning how to write and implement custom Lua scripts of your own to simulate
systems of an aircraft, with all plugin definitions available to you, including flyables.

## Building from source

1. Clone the latest documentation, found on GitHub:

```bash
   $ git clone --recursive https://github.com/filiastra/dcs-api-docs.git
```

2. Install the required dependencies:

```bash
   $ pip install -r requirements.txt 
```

3. Test build the documentation:

```bash
   $ cd docs/ && make html
```

## Documentation

Documentation is available [here](https://dcswd.rtfd.io/).

## Contributing

Check out the [contribution guidelines](CONTRIBUTING.md).