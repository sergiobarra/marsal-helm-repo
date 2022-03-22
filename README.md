# marsal-helm-repo
MARSAL He

### Install helm and others
```bash
# Install helm
sudo apt-get update && sudo apt-get upgrade -y
sudo apt-get install tree
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

Create helm charts and push to github repo
```bash
# Create example charts
helm create example-chart-1
helm create example-chart-2

mv example-chart-1 example-chart-2 charts/
helm repo index .
git push
```

Use helm repo
```bash
helm repo add marsal-helm-repo https://sergiobarra.github.io/marsal-helm-repo/
helm search repo marsal-helm-repo
helm install example2 marsal-helm-repo/example-chart-2
```