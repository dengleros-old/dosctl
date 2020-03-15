# build os


install dosctl to your PATH, change to a (empty) working directory
```
dosctl <YML-FILE>
```

# run os

Execute from the same working directory as above
```
dosctl run <YML-FILE>
```

# Build docker image

```
dosctl img dengleros/os-rustysd:latest -build -push
```
