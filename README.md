# kubernetes-command

    # delete terminated pod but not deleted, should be force
     kubectl delete pod <PODNAME> --grace-period=0 --force --namespace <NAMESPACE>
    # delete all objects in specific namespace
        kubectl delete --all pods --namespace=foo
        kubectl delete --all namespaces
        kubectl delete daemonsets,replicasets,services,deployments,pods,rc,ingress --all --all-namespaces
    # This command will delete all the namespaces except kube-system, which might be useful:
        for each in $(kubectl get ns -o jsonpath="{.items[*].metadata.name}" | grep -v kube-system);
        do
        kubectl delete ns $each
        done
    # command for get all pods status not running
        kubectl get po -n longhorn-system | grep -v "Running" 
    # command for check event
        kubectl get events --sort-by=.metadata.creationTimestamp
    # Force delete
        kubectl delete pod NAME --grace-period=0 --force
        and
        kubectl delete pod NAME --now
     # Force Delete PVC
         kubectl patch pvc jhooq-pv-claim -p '{"metadata":{"finalizers":null}}'
         and 
         kubectl delete pvc jhooq-pv-claim


