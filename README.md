# istio-port-forwading
port forwarding add-ons

jaeger:

kubectl --namespace istio-system \
    port-forward $(kubectl \
    --namespace istio-system \
    get pod \
    --selector app=jaeger \
    --output jsonpath='{.items[0].metadata.name}') \
    16686:16686 &
    
kiali:

kubectl --namespace istio-system     port-forward $(kubectl \
    --namespace istio-system \
    get pod \
    --selector app=kiali \
    --output jsonpath='{.items[0].metadata.name}') 20001:20001 &
