whiskeytap - A tool for generating a pgTAP test set from an existing database

# Usage

    whiskeytap -d testdb > tests.pg

    whiskeytap --dbname testdb --prefix t/100
    pg_prove -d testdb

# Description

`whiskeytap` is a command-line application to generate a
[pgTAP](http://pgtap.org/) test suite from a PostgreSQL database.

`whiskeytap` connects to a running database and generates pgTAP tests to cover
a subset of the schema. For each table it writes tests for each
column of the table, indexes, triggers, primary and foreign keys. It also
writes tests for non-table related objects: types, enums, sequences and
functions.

By default `whiskeytap` writes all tests to stdout, but if given a filename
prefix with the `--prefix` option it will write one test file for each
table and one test file for other objects.

# Options

    -d,  --dbname DBNAME         Database to which to connect.
    -U,  --username USERNAME     User with which to connect.
    -h,  --host HOST             Host to which to connect.
    -p,  --port PORT             Port to which to connect.
    -c,  --connect CONN          Connect to DBI data source instead of host/dbname

    -n   --schema SCHEMA         Process only objects in schemas matching SCHEMA
    -N   --exclude-schema SCHEMA Exclude objects in schemas matching SCHEMA
    -t,  --table TABLE           Process only tables matching TABLE
    -T,  --exclude-table TABLE   Exclude tables matching TABLE
    -s,  --use-schemas           Use schemas in generated tests
    -o,  --prefix PREFIX         Write tests to files starting with prefix
    -x,  --exclude-check CHECK   Don't generate pgTAP checks matching CHECK

    -H,  --help                  Print a usage statement and exit.
    -?,                          Print a usage statement and exit.
    -m,  --man                   Print the complete documentation and exit.
    -V,  --version               Print the version number and exit.

# Bugs

`whiskeytap` works with schemas I write, but hasn't been tested with
schemas with identifiers that need quoting. It likely quotes some
identifiers too much or not enough.

Test cases or patches welcome.

# Author

Steve Atkins <steve@wordtothewise.com>

[https://github.com/wttw/whiskeytap](https://github.com/wttw/whiskeytap)
[https://labs.wordtothewise.com/whiskeytap](https://labs.wordtothewise.com/whiskeytap)

# Copyright

Copyright (c) 2016 Steve Atkins. Released under Artistic License.
