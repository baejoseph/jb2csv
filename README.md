jb2csv
========

Converts a stream of newline separated json data to csv format.
This is a fork of json2csv, with a change of name, so as to avoid a clash with the node.js (NPM) function with the same name.

[![Build Status](https://travis-ci.org/jehiah/json2csv.png?branch=master)](https://travis-ci.org/jehiah/json2csv) [![GitHub release](https://img.shields.io/github/release/jehiah/json2csv.svg)](https://github.com/jehiah/json2csv/releases/latest)


Installation
============

pre-built binaries are available under [releases](https://github.com/jehiah/json2csv/releases).

If you have a working golang install, you can use `go get`.

```bash
go get github.com/baejoseph/jb2csv
```

Usage
=====

```
usage: jb2csv
    -k fields,and,nested.fields,to,output
    -i /path/to/input.json (optional; default is stdin)
    -o /path/to/output.csv (optional; default is stdout)
    --version
    -p print csv header row
    -h This help
```

To convert:

```json
{"user": {"name":"jehiah", "password": "root"}, "remote_ip": "127.0.0.1", "dt" : "[20/Aug/2010:01:12:44 -0400]"}
{"user": {"name":"jeroenjanssens", "password": "123"}, "remote_ip": "192.168.0.1", "dt" : "[20/Aug/2010:01:12:44 -0400]"}
{"user": {"name":"unknown", "password": ""}, "remote_ip": "76.216.210.0", "dt" : "[20/Aug/2010:01:12:45 -0400]"}
```

to:

```
"jehiah","127.0.0.1"
"jeroenjanssens","192.168.0.1"
"unknown","76.216.210.0"
```
    
you would either

```bash
jb2csv -k user.name,remote_ip -i input.json -o output.csv
```

or

```bash
cat input.json | jb2csv -k user.name,remote_ip > output.csv
```
