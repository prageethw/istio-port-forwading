# istio-port-forwading
port forwarding add-ons istio 1.5.1

`jaeger:`

kubectl --namespace istio-system \
    port-forward $(kubectl \
    --namespace istio-system \
    get pod \
    --selector app=jaeger \
    --output jsonpath='{.items[0].metadata.name}') \
    16686:16686 &
    
`kiali:`

kubectl --namespace istio-system     port-forward $(kubectl \
    --namespace istio-system \
    get pod \
    --selector app=kiali \
    --output jsonpath='{.items[0].metadata.name}') 20001:20001 &

`grafana:`

kubectl --namespace istio-system     port-forward $(kubectl \
    --namespace istio-system \
    get pod \
    --selector app=kiali \
    --output jsonpath='{.items[0].metadata.name}') 3000:3000 &
    
`prometheus`

kubectl --namespace istio-system     port-forward $(kubectl \
    --namespace istio-system \
    get pod \
    --selector app=prometheus \
    --output jsonpath='{.items[0].metadata.name}') 9000:9000 &
