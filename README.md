# SnowSQL Formatter CLI

A fork of [snowsql-formatter](https://github.com/Snowflake-Labs/snowsql-formatter) to add a CLI tool to the original package

New Features:

- Usage as CLI tool

**SQL Formatter** is a JavaScript library for pretty-printing SQL queries.
It started as a port of a [PHP Library][], but has since considerably diverged.
It supports [Standard SQL][], [Couchbase N1QL][], [IBM DB2][] and [Oracle PL/SQL][] dialects.

[Try the demo of the source of this fork.](https://kufii.github.io/sql-formatter-plus//)

## Install

Get the latest version from NPM:

```shell
npm install snowsql-formatter-cli
```

## Usage (from CLI)

The CLI tool will be installed under `snowsql-formatter`
and may be invoked via `npx snowsql-formatter`:

```sh
snowsql-formatter -h
```

```
usage: snowsql-formatter [-h] [-o OUTPUT] [-l {db2,mariadb,mysql,n1ql,plsql,postgresql,redshift,spark,sql,tsql}]
                     [-i N | -t] [-u] [--lines-between-queries N] [--version] [FILE]

SQL Formatter

positional arguments:
  FILE                  Input SQL file (defaults to stdin)

optional arguments:
  -h, --help            show this help message and exit
  -o OUTPUT, --output OUTPUT
                        File to write SQL output (defaults to stdout)
  -l {db2,mariadb,mysql,n1ql,plsql,postgresql,redshift,spark,sql,tsql},
  --language {db2,mariadb,mysql,n1ql,plsql,postgresql,redshift,spark,sql,tsql}
                        SQL Formatter dialect (defaults to basic sql)
  -i N, --indent N      Number of spaces to indent query blocks (defaults to 2)
  -t, --tab-indent      Indent query blocks with tabs instead of spaces
  -u, --uppercase       Capitalize language keywords
  --lines-between-queries N
                        How many newlines to insert between queries (separated by ";")
  --version             show program's version number and exit
```

By default, the tool takes queries from stdin and processes them to stdout but
one can also name an input file name or use the `--output` option.

```sh
echo 'select * from tbl where id = 3' | snowsql-formatter -u
```

```sql
SELECT
  *
FROM
  tbl
WHERE
  id = 3
```

Currently just four SQL dialects are supported:

- **sql** - [Standard SQL][]
- **n1ql** - [Couchbase N1QL][]
- **db2** - [IBM DB2][]
- **pl/sql** - [Oracle PL/SQL][]

## License

[MIT](https://github.com/Snowflake-Labs/snowsql-formatter/blob/master/LICENSE)

[php library]: https://github.com/jdorn/sql-formatter
[standard sql]: https://en.wikipedia.org/wiki/SQL:2011
[couchbase n1ql]: http://www.couchbase.com/n1ql
[ibm db2]: https://www.ibm.com/analytics/us/en/technology/db2/
[oracle pl/sql]: http://www.oracle.com/technetwork/database/features/plsql/index.html
