## create an operator from scratch
https://www.katacoda.com/akoserwal/scenarios/how-to-design-an-operator

```
mkdir -p $GOPATH/src/github.com/cluster-operator/
cd $GOPATH/src/github.com/cluster-operator/

operator-sdk init --domain=mjbower.com --repo=github.com/mjbower/cluster-operator
operator-sdk create api --group cache --version v1 --kind MaerskCluster --resource=true --controller=true


```

Let's Generate an API & Controller for our operator

Version: v1
group: Cache
Kind: MaerskCluster
Adding a controller for our Demoproduct API. Which will handle the logic to create or update the resoures.

API end-point exposed by our operator will look like: /apis/cache/v1/namespace/$NAMESPACE/maerskclusters/: maerskcluster

## add custom specs
modify `cluster-operator/api/v1/maerskcluster_types.go`

add 
```
    // Replicas determines the desired number of running demo product pods
    Replicas int32 `json:"replicas,omitempty"`
    // RouteHostName sets the host name to use on the Ingress or OpenShift Route
    RouteHostName string `json:"routeHostName,omitempty"
```

```
make generate
make manifests
```

## 

generated CRD
config/crd/bases/mjbower.com_maerskcluster.yaml


















