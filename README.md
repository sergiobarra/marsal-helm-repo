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

The whole thing should look like this when executing <code>tree</code> inside <code>/marsal-helm-repo</code>:
```bash
LICENSE
├── README.md
├── charts
│   ├── example-chart-1-0.1.0.tgz
│   ├── example-chart-2-0.1.0.tgz
│   ├── marsal-open5gs-1.0.0.tgz
│   └── marsal-open5gs-1.1.0.tgz
├── example-chart-1
│   ├── Chart.yaml
│   ├── templates
│   │   ├── ...
├── example-chart-2
│   ├── Chart.yaml
│   ├── templates
│   │   ├── ...
├── index.yaml
├── marsal-open5gs-v1.0
│   ├── Chart.yaml
│   ├── templates
│   │   ├── core
│   │   │   ├── NOTES.txt
│   │   │   ├── amf-cmap.yaml
│   │   │   ├── amf-depl.yaml
│   │   │   ├── ausf-cmap.yaml
│   │   │   ├── ausf-depl.yaml
│   │   │   ├── bsf-cmap.yaml
│   │   │   ├── bsf-depl.yaml
│   │   │   ├── mongodb.yaml
│   │   │   ├── nrf-cmap.yaml
│   │   │   ├── nrf-depl.yaml
│   │   │   ├── nssf-cmap.yaml
│   │   │   ├── nssf-depl.yaml
│   │   │   ├── pcf-cmap.yaml
│   │   │   ├── pcf-depl.yaml
│   │   │   ├── smf-cmap.yaml
│   │   │   ├── smf-depl.yaml
│   │   │   ├── udm-cmap.yaml
│   │   │   ├── udm-depl.yaml
│   │   │   ├── udr-cmap.yaml
│   │   │   ├── udr-depl.yaml
│   │   │   ├── upf-cmap.yaml
│   │   │   ├── upf-depl.yaml
│   │   │   └── webui-depl.yaml
│   │   ├── mec
│   │   │   ├── upfmec-cmap.yaml
│   │   │   └── upfmec-depl.yaml
│   │   └── monitor
│   │       └── amarisoft-sf-depl.yaml
│   └── values.yaml
└── ...
```

## Use helm repo

```bash
helm repo add marsal-helm-repo https://sergiobarra.github.io/marsal-helm-repo/
helm search repo marsal-helm-repo
helm install example2 marsal-helm-repo/example-chart-2
```