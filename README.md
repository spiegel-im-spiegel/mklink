# [ml] -- Make Link with Markdown Format

[![check vulns](https://github.com/spiegel-im-spiegel/ml/workflows/vulns/badge.svg)](https://github.com/spiegel-im-spiegel/ml/actions)
[![lint status](https://github.com/spiegel-im-spiegel/ml/workflows/lint/badge.svg)](https://github.com/spiegel-im-spiegel/ml/actions)
[![lint status](https://github.com/spiegel-im-spiegel/ml/workflows/build/badge.svg)](https://github.com/spiegel-im-spiegel/ml/actions)
[![GitHub license](https://img.shields.io/badge/license-Apache%202-blue.svg)](https://raw.githubusercontent.com/spiegel-im-spiegel/ml/master/LICENSE)
[![GitHub release](http://img.shields.io/github/release/spiegel-im-spiegel/ml.svg)](https://github.com/spiegel-im-spiegel/ml/releases/latest)

## Build and Install

```
$ go install github.com/spiegel-im-spiegel/gpgpdump@latest
```

## Binaries

See [latest release](https://github.com/spiegel-im-spiegel/ml/releases/latest).

## Usage

```
$ ml -h
Usage:
  ml [flags] [URL [URL]...]

Flags:
      --debug          for debug
  -h, --help           help for ml
  -i, --interactive    interactive mode
      --log string     output log
  -s, --style string   link style [markdown|wiki|html|csv|json] (default "markdown")
  -v, --version        output version of ml
```

```
$ ml https://git.io/vFR5M
[GitHub - spiegel-im-spiegel/ml: Make Link with Markdown Format](https://github.com/spiegel-im-spiegel/ml)
```

```
$ echo https://git.io/vFR5M | ml
[GitHub - spiegel-im-spiegel/ml: Make Link with Markdown Format](https://github.com/spiegel-im-spiegel/ml)
```

### Support Other Styles

```
$ ml -s html https://git.io/vFR5M
<a href="https://github.com/spiegel-im-spiegel/ml">GitHub - spiegel-im-spiegel/ml: Make Link with Markdown Format</a>
```

Support Styles: `markdown`, `wiki`, `html`, `csv`, `json`

### logging

```
$ ml --log log.txt https://git.io/vFR5M
[GitHub - spiegel-im-spiegel/ml: Make Link with Markdown Format](https://github.com/spiegel-im-spiegel/ml)

$ cat log.txt
[GitHub - spiegel-im-spiegel/ml: Make Link with Markdown Format](https://github.com/spiegel-im-spiegel/ml)
```

### Interactive Mode

```
$ ml -i
Input 'q' or 'quit' to stop
ml> https://git.io/vFR5M
[GitHub - spiegel-im-spiegel/ml: Make Link with Markdown Format](https://github.com/spiegel-im-spiegel/ml)
ml>
```

## With Go Codes

```go
package main

import (
    "context"
    "fmt"
    "io"
    "os"

    "github.com/spiegel-im-spiegel/ml/makelink"
)

func main() {
    lnk, err := makelink.New(context.Background(), "https://git.io/vFR5M")
    if err != nil {
        fmt.Fprintln(os.Stderr, err)
        return
    }
    _, _ = io.Copy(os.Stdout, lnk.Encode(makelink.StyleMarkdown))
    // Output:
    // [GitHub - spiegel-im-spiegel/ml: Make Link with Markdown Format](https://github.com/spiegel-im-spiegel/ml)
}
```

## Modules Requirement Graph

[![dependency.png](./dependency.png)](./dependency.png)

[ml]: https://github.com/spiegel-im-spiegel/ml "spiegel-im-spiegel/ml: Make Link with Markdown Format"
