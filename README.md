brew install fluxctl
helm repo add fluxcd https://charts.fluxcd.io
kubectl create ns fluxcd
kubectl apply -f https://raw.githubusercontent.com/fluxcd/helm-operator/master/deploy/crds.yaml
helm upgrade -i flux fluxcd/flux --wait --namespace fluxcd  --set git.url=git@github.com:zam-zam/k8s-addons.git
