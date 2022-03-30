# marsal-helm-repo
Repository containing the helm charts for the MARSAL project.

## Install helm and others
```bash
# Install helm
sudo apt-get update && sudo apt-get upgrade -y
sudo apt-get install tree
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

## Create helm charts
Create helm charts and push to github repo
```bash
# Create example charts
helm create example-chart-1
helm create example-chart-2
helm create marsal-open5gs

# Package helm charts
helm package marsal-open5gs-v1.1/

# See what the chart would install
helm install --dry-run debug marsal-open5gs-v1.1/

# Pacakged charts should be stored in charts directory
mv marsal-open5gs-1.1.0.tgz charts/

# Regenerate chart index
helm repo index .

# Push changes to repo
git add .
git commit -m "Commit message"
git push
```

## Use helm repo

```bash
helm repo add marsal-helm-repo https://sergiobarra.github.io/marsal-helm-repo/
helm search repo marsal-helm-repo
helm install example2 marsal-helm-repo/example-chart-2
```