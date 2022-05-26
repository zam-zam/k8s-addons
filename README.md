brew install fluxctl
helm repo add fluxcd https://charts.fluxcd.io
kubectl create ns fluxcd
kubectl apply -f https://raw.githubusercontent.com/fluxcd/helm-operator/master/deploy/crds.yaml
helm upgrade -i flux fluxcd/flux --wait --namespace fluxcd  --set git.url=https://github.com/zam-zam/k8s-addons.git
helm upgrade -i helm-operator fluxcd/helm-operator --wait \
    --namespace fluxcd \
    --set git.ssh.secretName=flux-git-deploy \
    --set helm.versions=v3
