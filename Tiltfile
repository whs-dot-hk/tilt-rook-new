allow_k8s_contexts('kubernetes-admin@cluster.local')
analytics_settings(enable = False)

def create_namespace(name):
    k8s_yaml(blob("""apiVersion: v1
kind: Namespace
metadata:
  name: %s
""" % name))

name = "rook-ceph"

create_namespace(name)

k8s_yaml(helm("charts/rook-ceph", name = "%s-operator" % name, namespace = name))
k8s_yaml(helm("charts/rook-ceph-cluster", name = "%s-cluster" % name, namespace = name, values = "cluster.values.yaml"))
