---
icon: flask-vial
---

# Lab 03 - Manage Azure resources by using Azure Resource Manager Templates

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-23 09-34-27.png" alt=""><figcaption></figcaption></figure>

## Task 01

### Go To Disks

<figure><img src="../../.gitbook/assets/Screenshot from 2025-03-03 19-29-20.png" alt=""><figcaption></figcaption></figure>

### Create a New Managed Disk

<figure><img src="../../.gitbook/assets/Screenshot from 2025-03-03 19-31-21.png" alt=""><figcaption></figcaption></figure>

### Select The Disk

<figure><img src="../../.gitbook/assets/Screenshot from 2025-03-03 19-35-14.png" alt=""><figcaption></figcaption></figure>

## Task 02

### Download the Template and Change Names and Depoly

<figure><img src="../../.gitbook/assets/Screenshot from 2025-03-03 19-35-55.png" alt=""><figcaption></figcaption></figure>

## Task 03

```
 az deployment group create --resource-group Resourse_Grp_name --template-file template.json --parameters parameters.json
```

<figure><img src="../../.gitbook/assets/Screenshot from 2025-03-03 20-11-09.png" alt=""><figcaption></figcaption></figure>



<figure><img src="../../.gitbook/assets/Screenshot from 2025-03-03 20-12-49.png" alt=""><figcaption></figcaption></figure>

## Task 04

### Use Below to Deploy With a New Resourse Group

```
 New-AzResourceGroupDeployment --ResourceGroupName Resourse_Grp_name --TemplateFile template.json --Parameter parameters.json
```

### Use Below to Deploy With a Already Existing Resourse Group

```
 az deployment group create --ResourceGroupName Resourse_Grp_name --TemplateFile template.json --Parameter parameters.json
```

<figure><img src="../../.gitbook/assets/Screenshot from 2025-03-03 20-20-59.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot from 2025-03-03 20-21-32.png" alt=""><figcaption></figcaption></figure>

## All Deployed Disks&#x20;

<figure><img src="../../.gitbook/assets/Screenshot from 2025-03-03 20-22-27.png" alt=""><figcaption></figcaption></figure>
