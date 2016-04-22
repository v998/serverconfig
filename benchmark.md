# Benchmarking OpenSSL

With custom built OpenSSL, it should be faster than the system-provided one.

Use these commands to have a check.

## Without AES acceleration

```
OPENSSL_ia32cap="~0x200000200000000" openssl speed -elapsed -evp aes-128-gcm
OPENSSL_ia32cap="~0x200000200000000" openssl speed -elapsed chacha20-poly1305
OPENSSL_ia32cap="~0x200000200000000" openssl speed -elapsed ecdhp256
```

## With AES acceleration (if the CPU support it!)

```
openssl speed -elapsed -evp aes-128-gcm
openssl speed -elapsed chacha20-poly1305
openssl speed -elapsed ecdhp256
```
