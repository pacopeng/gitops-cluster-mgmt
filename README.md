# Red Hat Summit 2023 GitOps Lab Resources

These are Kubernetes/OpenShift resources used as part of the lab found at https://github.com/redhat-scholars/summit-2023-gitops-lab-guide.

https://redhat-scholars.github.io/summit-2023-gitops-lab-guide/summit-2023-gitops-workshop-guide/main/m1-overview/intro.html


oc adm policy add-cluster-role-to-user cluster-admin system:serviceaccount:openshift-gitops:openshift-gitops-argocd-application-controller

oc get cm argocd-rbac-cm -o yaml -n openshift-gitops


export ARGO_PASSWORD=$(oc get secret openshift-gitops-cluster -o json -n openshift-gitops | jq '.data["admin.password"]' -r | base64 --decode)

argocd login openshift-gitops-server-openshift-gitops.apps.test.lab.local \
--insecure \
--username admin \
--password $ARGO_PASSWORD


https://cloud.redhat.com/blog/your-guide-to-continuous-delivery-with-openshift-gitops-and-kustomize


https://cloud.redhat.com/blog/a-guide-to-using-gitops-and-argocd-with-rbac



https://developer.ibm.com/blogs/gitops-best-practices-for-the-real-world/

https://developer.ibm.com/articles/gitops-process-reference-implementation/



https://cloud.redhat.com/blog/helm-based-applications-on-red-hat-advanced-cluster-manager-and-openshift-gitops




oc secrets link --for=pull,mount default quay -n go-hello-dev
oc secrets link --for=pull,mount builder quay -n go-hello-dev
oc secrets link --for=pull,mount pipeline quay -n go-hello-dev
oc secrets link --for=pull,mount deployer quay -n go-hello-dev
oc secrets link --for=pull,mount go-hello-helm-app-dev-gohello quay -n go-hello-dev


oc secrets link default gitlab -n go-hello-dev
oc secrets link builder gitlab -n go-hello-dev
oc secret  link pipeline gitlab -n go-hello-dev
oc secret  link deployer gitlab -n go-hello-dev
oc secrets link  go-hello-helm-app-dev-gohello gitlab -n go-hello-dev




oc secrets link --for=pull,mount default quay -n go-hello-prod
oc secrets link --for=pull,mount builder quay -n go-hello-prod
oc secrets link --for=pull,mount pipeline quay -n go-hello-prod
oc secrets link --for=pull,mount deployer quay -n go-hello-prod
oc secrets link --for=pull,mount go-hello-helm-app-prod-gohello quay -n go-hello-prod



oc secrets link default gitlab -n go-hello-prod
oc secrets link builder gitlab -n go-hello-prod
oc secrets link pipeline gitlab -n go-hello-prod
oc secrets link deployer gitlab -n go-hello-prod
oc secrets link go-hello-helm-app-prod-gohello gitlab -n go-hello-prod