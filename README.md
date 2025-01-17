# karaoke-gitops-flux

## Set GITHUB_TOKEN environment varialble
```
export GITHUB_TOKEN=github_pat_****
```

## Bootstrap staging

1. Create kind k8s cluster:

```
kind create cluster --name karaoke-staging
```

2. Bootstrap flux

```
flux bootstrap github \
  --owner=lukewyman \
  --repository=karaoke-gitops-flux \
  --branch=main \
  --path=./clusters/staging \
  --personal
```

## Bootstrap production

1. Create kind k8s cluster:

```
kind create cluster --name karaoke-production
```

2. Bootstrap flux

```
flux bootstrap github \
  --owner=lukewyman \
  --repository=karaoke-gitops-flux \
  --branch=main \
  --path=./clusters/production \
  --personal
```