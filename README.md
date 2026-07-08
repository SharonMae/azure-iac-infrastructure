# Azure IaC Infrastructure

Azure IaC Infrastructure è un progetto dedicato all'implementazione di infrastrutture cloud su Microsoft Azure mediante il paradigma Infrastructure as Code (IaC).

L'obiettivo del repository è automatizzare il provisioning delle risorse Azure, garantendo configurazioni ripetibili, versionabili e facilmente manutenibili.

Il progetto rappresenta una base per la gestione dell'infrastruttura cloud secondo le best practice DevOps, favorendo automazione, scalabilità e controllo delle modifiche attraverso Git.

Il repository mette a confronto tre approcci differenti per provisionare la stessa infrastruttura (VM Linux con rete, IP pubblico e NSG dedicati): Terraform , Bicep e Ansible.

---

## Obiettivi del progetto

- Automatizzare il provisioning delle risorse Azure.
- Gestire l'infrastruttura come codice (Infrastructure as Code).
- Rendere le configurazioni versionabili tramite Git.
- Facilitare il rilascio di ambienti riproducibili.
- Confrontare strumenti IaC differenti (Terraform, Bicep, Ansible) a parità di scenario.
- Adottare un approccio modulare e scalabile per futuri sviluppi.

---

## Tecnologie utilizzate

Terraform
Bicep (Azure Resource Manager - ARM)
Ansible
Microsoft Azure
Azure CLI
YAML
Git & GitHub

---

## Struttura del repository

```text
azure-iac-infrastructure/
│
├── azure_vm.tf # Configurazione Terraform della Virtual Machine
├── azure_vm.bicep # Configurazione Bicep (ARM) della Virtual Machine
├── azure_vm.yml# Playbook Ansible per il provisioning della Virtual Machine
├── README.md# Documentazione del progetto
└── .gitignore
```

---

## Prerequisiti

Per utilizzare il progetto sono necessari:

- Terraform installato
- Azure CLI (include il supporto nativo a Bicep)
- Ansible installato, con la collection `azure.azcollection` per i moduli `azure_rm_*`
- Un account Microsoft Azure con una sottoscrizione attiva
- Git

---

## Utilizzo

### 1. Clonare il repository

```bash
git clone https://github.com/<username>/azure-iac-infrastructure.git
cd azure-iac-infrastructure
```

### 2. Autenticarsi su Azure

```bash
az login
```

### Opzione A — Provisioning con Terraform

```bash
# Inizializzare Terraform
terraform init

# Verificare il piano di esecuzione
terraform plan

# Distribuire l'infrastruttura
terraform apply
```

### Opzione B — Provisioning con Bicep

Il file `azure_vm.bicep` definisce NSG, VNet, Subnet, IP pubblico, NIC e VM Linux (Ubuntu 22.04 LTS). Richiede una Resource Group già esistente e il parametro `adminPassword`.

```bash
# Creare (se non esiste già) il resource group di destinazione
az group create --name myResourceGroup --location westeurope

# Validare il template
az deployment group validate \
- --resource-group myResourceGroup \
- --template-file azure_vm.bicep \
- --parameters adminPassword=<password-sicura>

# Distribuire l'infrastruttura
az deployment group create \
- --resource-group myResourceGroup \
- --template-file azure_vm.bicep \
- --parameters adminPassword=<password-sicura>
```

Parametri principali esposti dal template:

| Parametro | Descrizione- | Default|
|-----------------|---------------------------------------|---------------------|
| `vmName`- | Nome della VM| `vm-web-01` |
| `location`| Region Azure | location del resource group |
| `adminUsername` | Username amministratore- | `azureuser` |
| `adminPassword` | Password amministratore (`@secure`)- | *obbligatorio* |

### Opzione C — Provisioning con Ansible

```bash
ansible-playbook azure_vm.yml
```

> Prima dell'esecuzione, sostituire il placeholder `INSERISCI_LA_TUA_CHIAVE_SSH` nel file `azure_vm.yml` con la propria chiave pubblica SSH.

---

## Caratteristiche

- Provisioning automatico delle risorse Azure.
- Tre implementazioni equivalenti (Terraform, Bicep, Ansible) dello stesso scenario infrastrutturale.
- Configurazione di rete completa: VNet, Subnet, NSG, IP pubblico e NIC.
- Infrastruttura completamente versionata con Git.
- Codice facilmente estendibile e manutenibile.
- Struttura predisposta per l'integrazione con pipeline CI/CD.

---

## Sviluppi futuri

Il repository potrà essere ampliato con:

- Storage Account
- Azure Key Vault
- Managed Identity
- Terraform Modules / Bicep Modules
- Pipeline GitHub Actions o Azure DevOps
- Gestione di ambienti multipli (Development, Test, Production)
- Autenticazione via chiave SSH anche per gli script Terraform e Bicep

---

## Best Practice adottate

- Infrastructure as Code (IaC)
- Versionamento tramite Git
- Configurazioni dichiarative
- Automazione del provisioning
- Repository organizzato e documentato
- Approccio orientato alla scalabilità

---
 
## Note

Progetto realizzato a scopo di studio, sperimentazione e consolidamento delle competenze in ambito Cloud Computing, Microsoft Azure, Terraform, Bicep e DevOps.

---
