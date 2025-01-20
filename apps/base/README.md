## Create the GitRepository for karaoke-helm
```
flux create source git karaoke-helm \
--url=https://github.com/lukewyman/karaoke-helm \
--branch=main --interval=5m \
--namespace=karaoke \
--export > ./apps/base/repository.yaml
```

## Create the HelmRelease for the song-library microservice
```
flux create helmrelease song-library \
--namespace=karaoke \
--interval=10m \
--source=GitRepository/karaoke-helm \
--chart=./song-library \
--export > ./apps/base/song-library/release.yaml
```

## Create the HelmRelease for the singers microservice
```
flux create helmrelease singers \
--namespace=karaoke \
--interval=10m \
--source=GitRepository/karaoke-helm \
--chart=./singers \
--export > ./apps/base/singers/release.yaml
```

## Create the HelmRelease for the rotations microservice
```
flux create helmrelease rotations \
--namespace=karaoke \
--interval=10m \
--source=GitRepository/karaoke-helm \
--chart=./rotations \
--export > ./apps/base/rotations/release.yaml
```

## Create the HelmRelease for the song-choices microservice
```
flux create helmrelease song-choices \
--namespace=karaoke \
--interval=10m \
--source=GitRepository/karaoke-helm \
--chart=./song-choices \
--export > ./apps/base/song-choices/release.yaml
```