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

helm create marsal-open5gs

helm package open5gs/

helm install --dry-run debug open5gs/


mv example-chart-1 example-chart-2 charts/
helm repo index .

git add .
git commit -m "Commit message"
git push
```

Use helm repo
```bash
helm repo add marsal-helm-repo https://sergiobarra.github.io/marsal-helm-repo/
helm search repo marsal-helm-repo
helm install example2 marsal-helm-repo/example-chart-2
```


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