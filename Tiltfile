load('ext://namespace', 'namespace_create', 'namespace_inject')

namespace_create('ambassador')

k8s_yaml('ambassador-operator-crds.yaml')
k8s_yaml(namespace_inject('ambassador-operator-kind.yaml', 'ambassador'))
k8s_yaml('ingress-example.yaml')

k8s_resource('ambassador-operator', objects=[
    'ambassadorinstallations.getambassador.io:customresourcedefinition',
    'ambassador-operator:serviceaccount',
    'ambassador-operator:role',
    'ambassador-operator-cluster:clusterrole',
    'ambassador-operator:rolebinding',
    'ambassador-operator-cluster:clusterrolebinding',
    'static-helm-values:configmap',
    'ambassador:ambassadorinstallation',
])

k8s_resource(new_name='ingress', objects=['example-ingress'], resource_deps=['ambassador-operator'])