# Building OpenSSL

## 0. Use newer gcc

For example, on CentOS 6, install `devtoolset-3-gcc` which is at 4.9.1.

It is much newer than the `gcc-4.4` provided by CentOS repo, and the `gcc-4.9.1` will allow building on x86-64 CPUs that supports AVX2, and other features that will accelerate the crypto process.


## 1. Download OpenSSL

Go to https://www.openssl.org/source/ and 

```
wget ...
tar xvf ...
cd ...
```

## 2. Download Chacha20-Poly1305 patch

Go to https://github.com/cloudflare/sslconfig/tree/master/patches and `wget ...`

## 3. Apply the chacha20 patch

`patch -p1 < ...`

## 4. Configure

`./config shared --prefix=/usr/local --openssldir=/usr/local/openssl -march=native`

## 5. Build

```
make depend # Because on OpenSSL 1.0.2g, it asks for make depend
make
make test
```

## 6. Install

`make install`

## 7. Check version

`openssl version`
