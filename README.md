# gocryptfs

Fork of [OJFord/docker-gocryptfs](https://github.com/OJFord/docker-gocryptfs) with ability to set your own UID/GID via environment variables.

All credit for the file-system itself to rfjakob/gocryptfs.

## Usage

Passphrase should be specified in:
```
$GOCRYPTFS_PSWD
```

CIPHERDIRs should be mounted under:
```
/crypts/
```

By default a flat structure is assumed, so that each first level directory should be a CIPHERDIR, instead, a list may be given at:
```
/etc/gocryptfs/crypts
```

The decrypted file-systems will be mounted symmetrically at:
```
/mnt/
```

`fusermount -u` is *not* run automatically.

## Environment Variables

- **UID** Owner user id, defaults to 10001
- **GID** Owner group id, defaults to 10001

User id and group id set usually only affects new files created, not existing files (existing file ownership are taken from the encrypted files). The `force_owner` option is not used.

Note: The container runs as root to be able to change to any user id at runtime.

## Licence

MIT.
