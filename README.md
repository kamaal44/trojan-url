# trojan-url

A tool for encoding and decoding trojan URLs from and to trojan config.

## URL Scheme

The trojan URL scheme is defined (not finalized) as such:

```
trojan://password@remote_host:remote_port
```

in which the password is url-encoded in case it contains illegal characters.

## Usage

```
$ ./trojan-url.py -h
usage: trojan-url.py [-h] [-d] [-q] [-i in_file] [-o out_file]

Encode and decode trojan URLs from and to trojan config.

optional arguments:
  -h, --help            show this help message and exit
  -d, --decode          decode input
  -q, --qrcode          output qrcode
  -i in_file, --input in_file
                        input file (default: "-" for stdin)
  -o out_file, --output out_file
                        output file (default: "-" for stdout)
```

## Examples

## Encode

### Normal

```
$ ./trojan-url.py -i /usr/share/doc/trojan/examples/client.json-example
trojan://password1@example.com:443
```

### QRCode

```
$ ./trojan-url.py -q -i /usr/share/doc/trojan/examples/client.json-example -o example.png
```

![](example.png)

## Decode

```
$ ./trojan-url.py -d
trojan://password1@example.com:443
{
    "run_type": "client",
    "local_addr": "127.0.0.1",
    "local_port": 1080,
    "remote_addr": "example.com",
    "remote_port": 443,
    "password": [
        "password1"
    ],
    "append_payload": true,
    "log_level": 1,
    "ssl": {
        "verify": true,
        "verify_hostname": true,
        "cert": "",
        "cipher": "ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES25
6-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES128-SHA:ECDHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA:DHE-
RSA-AES256-SHA:AES128-SHA:AES256-SHA:DES-CBC3-SHA",
        "sni": "example.com",
        "alpn": [
            "h2",
            "http/1.1"
        ],
        "reuse_session": true,
        "curves": "",
        "sigalgs": ""
    },
    "tcp": {
        "keep_alive": true,
        "no_delay": true,
        "fast_open": true,
        "fast_open_qlen": 5
    }
}
```
