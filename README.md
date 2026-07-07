# Azure IaC Infrastructure

 Azure IaC Infrastructure  è un progetto dedicato all'implementazione di infrastrutture cloud su  Microsoft Azure  mediante il paradigma  Infrastructure as Code (IaC) .

L'obiettivo del repository è automatizzare il provisioning delle risorse Azure utilizzando  Terraform , garantendo configurazioni ripetibili, versionabili e facilmente manutenibili.

Il progetto rappresenta una base per la gestione dell'infrastruttura cloud secondo le best practice DevOps, favorendo automazione, scalabilità e controllo delle modifiche attraverso Git.

---

## Obiettivi del progetto

  Automatizzare il provisioning delle risorse Azure.
  Gestire l'infrastruttura come codice (Infrastructure as Code).
  Rendere le configurazioni versionabili tramite Git.
  Facilitare il rilascio di ambienti riproducibili.
  Adottare un approccio modulare e scalabile per futuri sviluppi.

---

## Tecnologie utilizzate

   Terraform 
   Microsoft Azure 
   Azure CLI 
   YAML 
   Git & GitHub 

---

## Struttura del repository

```text
azure-iac-infrastructure/
│
├── azure_vm.tf          # Configurazione Terraform della Virtual Machine
├── azure_vm.yml         # File di configurazione YAML
├── README.md            # Documentazione del progetto
└── .gitignore
```

---

## Prerequisiti

Per utilizzare il progetto sono necessari:

  Terraform installato
  Azure CLI
  Un account Microsoft Azure con una sottoscrizione attiva
  Git

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

### 3. Inizializzare Terraform

```bash
terraform init
```

### 4. Verificare il piano di esecuzione

```bash
terraform plan
```

### 5. Distribuire l'infrastruttura

```bash
terraform apply
```

---

## Caratteristiche

  Provisioning automatico delle risorse Azure.
  Configurazione dell'infrastruttura tramite Terraform.
  Infrastruttura completamente versionata con Git.
  Codice facilmente estendibile e manutenibile.
  Struttura predisposta per l'integrazione con pipeline CI/CD.

---

## Sviluppi futuri

Il repository potrà essere ampliato con:

  Virtual Network (VNet)
  Subnet
  Network Security Groups (NSG)
  Public IP
  Storage Account
  Azure Key Vault
  Managed Identity
  Terraform Modules
  Pipeline GitHub Actions o Azure DevOps
  Gestione di ambienti multipli (Development, Test, Production)

---

## Best Practice adottate

  Infrastructure as Code (IaC)
  Versionamento tramite Git
  Configurazioni dichiarative
  Automazione del provisioning
  Repository organizzato e documentato
  Approccio orientato alla scalabilità

---

## 

Progetto realizzato a scopo di studio, sperimentazione e consolidamento delle competenze in ambito Cloud Computing, Microsoft Azure, Terraform e  DevOps.

---
