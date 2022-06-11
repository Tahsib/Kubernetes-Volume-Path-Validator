# Kubernetes Volume Validator

Automated Policy check to restrict volume path for deployment manifests.


# Usage

## Install Datree's CLI integration

```
curl https://get.datree.io | /bin/bash
```

## Create a free Datree account
```
https://app.datree.io/login
```

## Connect using Token

Login to your account and go to "SETTINGS" (from right-up-corner) and get the token, then

### Store token in config file

```
echo "token: <TOKEN>" > ~/.datree/config.yaml
```

### (Or) Add to Environment variable
```
export DATREE_TOKEN=<TOKEN>
```

## Publish the custom policy for volume

Add the volume prefix for the solution in the `policies.yaml` file

```
....
....
glusterfs:
    properties:
        path:
            type: string
            pattern: ^/<volume-prefix-for-the-solution>/*$        
```

then run,

```
datree publish policies.yaml
```

## Check volume paths of deployments

```
datree test *.yml --only-k8s-files 
```
