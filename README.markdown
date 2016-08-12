# catacomb

Our fork of https://github.com/twe4ked/catacomb/

Encrypts content using the nominated public key, either found locally or otherwise sourced from GitHub.
Encrypted files can then be decrypted using the matching `~/.ssh/id_rsa`.

Public keys must be in the RSA format as produced by openssh, e.g.

    ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQB/nAmOjTmezNUDKYvEeIRf2YnwM9/uUG1d0BYsc8/tRtx+RGi7N2lUbp728MXGwdnL9od4cItzky/zVdLZE2cycOa18xBK9cOWmcKS0A8FYBxEQWJ/q9YVUgZbFKfYGaGQxsER+A0w/fX8ALuk78ktP31K69LcQgxIsl7rNzxsoOQKJ/CIxOGMMxczYTiEoLvQhapFQMs3FL96didKr/QbrfB1WT6s3838SEaXfgZvLef1YB2xmfhbT9OXFE3FXvh2UPBfN+ffE7iiayQf/2XR+8j4N4bW30DiPtOQLGUrH1y5X/rpNZNlWW2+jGIxqZtgWg7lTy3mXy5x836Sj/6L

Note the major limitation that this can only be used to encrypt files that are smaller than the length of the key used for encryption.

For other solutions, you may want to try:
* https://www.npmjs.com/package/node-rsa

## Installation

``` sh
curl https://raw.github.com/twe4ked/catacomb/master/bin/catacomb > catacomb \
    && chmod u+x catacomb \
    && ./catacomb --help
```

## Requirements

* openssl
* ssh-keygen

## Usage

### Encrypting

``` sh
catacomb $RECIPIENTS_GITHUB_USERNAME < file.txt > encrypted.txt
```

If `$RECIPIENTS_GITHUB_USERNAME` exists locally (`$HOME/.ssh/${RECIPIENTS_GITHUB_USERNAME}.pub`) use it to encrypt the content, otherwise go looking for their public key on github (`https://github.com/${RECIPIENTS_GITHUB_USERNAME}.keys`) and save it locally.

### Decrypting

``` sh
catacomb < encrypted.txt
```

## Notes

* Encrypts using the first key retrieved from GitHub
* Decrypts using `~/.ssh/id_rsa`

## Licence

MIT.

[fresh]: https://github.com/freshshell/fresh
