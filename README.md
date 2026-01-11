SCION End Host Bootstrap Server
===============================

A simple SCION end host bootstrap server for testing purposes. Serves TRCs and a JSON topology
definition via HTTP/1.1.

More information on SCION bootstrapping:
- https://github.com/netsec-ethz/bootstrapper
- https://github.com/netsys-lab/bootstrap-server

## Usage ##

There are no dependencies beyond the Python standard library. Just run download and run
[bootstrap-server.py](./bootstrap-server.py). The server expects three mandatory arguments, a path
to the AS configuration directory, a bind IP and the server port.

The AS configurations directory must contain the topology definition as `./topology.json` and a
directory called `certs` that contains the TRC(s). TRCs must follow the naming scheme
`ISD{isd}-B{base}-S{serial}.trc`, where `{isd}` is the decimal ISD number, and `{base}` and
`{serial}` are decimal numbers identifying the version of the TRC. Not that the file names use
upper case letters. The expected directory structure is identical to the output of the `scion.sh`
script from the [SCION repository](https://github.com/scionproto/scion).

If you need an HTTPS bootstrap server, place a reverse proxy in front of the script.
