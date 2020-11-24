# typescript

# How to see content of a last layer
```bash
$ docker inspect -f "{{json .RootFS.Layers}}" lrozek/typescript:latest | jq .[length-1]
"sha256:997e1e18e0eb705da7707b0e79f4e117e98d0ecdbae20c6bb4cc3168471a8128"
$ sudo cd /var/lib/docker
$ grep -lir 997e1e18e0eb705da7707b0e79f4e117e98d0ecdbae20c6bb4cc3168471a8128
image/aufs/layerdb/sha256/faaf5b67e9c4270746e549273516d061f49c74a237dc51d135da36a7005563e8/diff
image/aufs/imagedb/content/sha256/e02b95f9241508a97d28c5cff2112531b6713c2689e7c4a8b657e3cf90eeae9e
image/aufs/distribution/diffid-by-digest/sha256/1f88f7b240c2837b7703403bd67cfc3f634aabd23d93ab7731cef7f7274f84b7
$ cat image/aufs/layerdb/sha256/faaf5b67e9c4270746e549273516d061f49c74a237dc51d135da36a7005563e8/cache-id
5884ca99e3cdefeedb764a008a227e1cff94b68615833986f7a05378d54add17
$ cd aufs/diff/5884ca99e3cdefeedb764a008a227e1cff94b68615833986f7a05378d54add17
```

More info can be found at https://stackoverflow.com/a/43094903
