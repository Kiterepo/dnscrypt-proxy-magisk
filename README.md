# dnscrypt-proxy for Android

A flexible DNS proxy, with support for modern encrypted DNS protocols such as [DNSCrypt v2](https://github.com/DNSCrypt/dnscrypt-protocol/blob/master/DNSCRYPT-V2-PROTOCOL.txt) and [DNS-over-HTTP/2](https://tools.ietf.org/html/draft-ietf-doh-dns-over-https-03).

## Features
- arm, arm64, x86 and x86_64 are supported.
- ipv4 and ipv6 are supported.
- All binary files are downloaded from [https://github.com/DNSCrypt/dnscrypt-proxy/releases](https://github.com/DNSCrypt/dnscrypt-proxy/releases)

## Installation
- Download the module, check it by public key (*gpg --keyserver keys.gnupg.net --recv-keys 17741F73276EC79CDB9F1F92C916DEFF84E8181B*) and flash it in Magisk Manager App or in Recovery.

### Set DNS server manually with 3rd-party app (not included in this module)
- DNS server address is 127.0.0.1:5354 for ipv4 and [::1]:5354 for ipv6
- If you use AfWall, you can write this enter custom script
  ```
  iptables -t nat -A OUTPUT -p tcp ! -d 9.9.9.9 --dport 53 -j DNAT --to-destination 127.0.0.1:5354
  iptables -t nat -A OUTPUT -p udp ! -d 9.9.9.9 --dport 53 -j DNAT --to-destination 127.0.0.1:5354
   ```
  and this shutdown script
  ```
  iptables -t nat -D OUTPUT -p tcp ! -d 9.9.9.9 --dport 53 -j DNAT --to-destination 127.0.0.1:5354
  iptables -t nat -D OUTPUT -p udp ! -d 9.9.9.9 --dport 53 -j DNAT --to-destination 127.0.0.1:5354
    ```

## Configuration (post-installing)
- Configuration located on `/sdcard/dnscrypt-proxy/dnscrypt-proxy.toml` [or /data/media/0/dnscrypt-proxy/dnscrypt-proxy.toml]
- For more detailed configuration please refer to [official documentation](https://github.com/DNSCrypt/dnscrypt-proxy/wiki/Configuration)

## Changelog
### v1.0.0
- updated binary & configuration files to 2.0.27
- updated configuration file [dnscrypt.toml] according to the revision https://github.com/DNSCrypt/dnscrypt-proxy/releases/tag/2.0.27
### v1.0.1
- updated binary files to 2.0.28
### v1.0.2
- updated binary files to 2.0.33

[Full changelog](changelog.md)

## Credit
- DNSCrypt-Proxy2 upstream | [jedisct1](https://github.com/DNSCrypt/dnscrypt-proxy)
- [bluemeda](https://github.com/bluemeda) for the original module
- [All contributor](https://github.com/Magisk-Modules-Repo/dnscrypt-proxy/graphs/contributors)
