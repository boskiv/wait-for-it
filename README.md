# [wait-for-it](https://pypi.org/project/wait-for-it/)

[![PyPi release](https://img.shields.io/pypi/v/wait-for-it.svg)](https://pypi.org/project/wait-for-it/)

Wait for service(s) to be available before executing a command.
`wait-for-it` is a script that will wait on the availability of one or more TCP host:port services before executing a user-defined command.
It is useful for synchronizing the spin-up of interdependent services, such as linked docker containers.

## Installation

```bash
$ pip install wait-for-it
```

## Usage
```bash
Usage: wait-for-it [OPTIONS] [COMMANDS]...

  Wait for service(s) to be available before executing a command.

Options:
  -h, --help               Show this message and exit.
  -v, --version            Show the version and exit.
  -q, --quiet              Do not output any status messages
  -s, --service host:port  Services to test, in the format host:port
  -t, --timeout seconds    Timeout in seconds, 0 for no timeout  [default: 15]
```

## Examples

Test to see if we can access port 80 on www.google.com, and if it is available, echo the message **google is up**:

```bash
$ wait-for-it \
--service www.google.com:80 \
-- echo "google is up"
```

```txt
waiting 15 seconds for www.google.com:80
www.google.com:80 is available after 0 seconds
google is up
```

You can set your own timeout with the `-t` or `--timeout` option. Setting the timeout value to **0** will disable the timeout:

```bash
$ wait-for-it \
--service www.google.com:80 \
--timeout 0 \
-- echo "google is up"
```

```txt
waiting for www.google.com:80 without a timeout
www.google.com:80 is available after 0 seconds
google is up
```

Multiple services can be tested by adding additional `-s` or `--service` options:

```bash
$ wait-for-it \
--service www.google.com:80 \
--service www.bing.com:80 \
--service www.duckduckgo.com:80 \
-- echo "google, bing, and duckduckgo are up"
```

```txt
waiting 15 seconds for www.google.com:80
www.google.com:80 is available after 0 seconds
waiting 15 seconds for www.bing.com:80
www.bing.com:80 is available after 0 seconds
waiting 15 seconds for www.duckduckgo.com:80
www.duckduckgo.com:80 is available after 0 seconds
google, bing, and duckduckgo are up
```

Status message output can be suppressed with the `-q` or `--quiet` option:

```bash
$ wait-for-it \
--quiet \
--service www.google.com:80 \
-- echo "google is up"
```

```txt
google is up
```

## Related
* [vishnubob/wait-for-it](https://github.com/vishnubob/wait-for-it)

## License

MIT &copy; [**Travis Clarke**](https://blog.travismclarke.com/)
