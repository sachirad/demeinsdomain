---
icon: flask-vial
---

# Lab-02-A:   Manage Subscription & RBAC

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-04 21-52-00.png" alt=""><figcaption><p>Lab-02-A Question</p></figcaption></figure>



## Go to Management Groups

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-05 08-49-21.png" alt=""><figcaption></figcaption></figure>

## Create a Management Group

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-05 08-51-56.png" alt=""><figcaption></figcaption></figure>

## Add subscription&#x20;

Since i have a subscription i moved it to the management group that we created

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-05 08-52-50.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-05 08-53-06.png" alt=""><figcaption></figcaption></figure>

## Assign a Bluilt-in Azure Role

#### Management Group > Access Control (IAM) > Add > Add role Assignment

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-10 12-41-32.png" alt=""><figcaption></figcaption></figure>

#### Search for <kbd>Virtual Machine Contributor</kbd> and click on it

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-10 12-42-38.png" alt=""><figcaption></figcaption></figure>

#### Click on Select Members and Add the <kbd>`helpdesk`</kbd> Group

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-10 12-49-04.png" alt=""><figcaption></figcaption></figure>

## Creating a Custom Role

#### Management Group > Access Control (IAM) > Add > Add Custom Role

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-10 12-50-38.png" alt=""><figcaption></figcaption></figure>

#### select <kbd>Clone</kbd> a role and select the role <kbd>Support Request Contributer</kbd>

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-10 12-52-42.png" alt=""><figcaption></figcaption></figure>

#### Click on <kbd>Exclude Permissions</kbd> and search for <kbd>Microsoft.Support</kbd>

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-10 12-54-12.png" alt=""><figcaption></figcaption></figure>

#### Click <kbd>Register Support Resource Provider</kbd>  > Add

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-10 12-56-06.png" alt=""><figcaption></figcaption></figure>

#### Select the Management Group as the Scope

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-10 12-56-48.png" alt=""><figcaption></figcaption></figure>

## Assign Custom Role

#### Just like adding a Build-In role search for the custom role and Add

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-10 13-00-17.png" alt=""><figcaption></figcaption></figure>

## RBAC (Roal Base Access Control)&#x20;

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-10 13-01-05.png" alt=""><figcaption></figcaption></figure>

## Monitor Activity Log

#### Management Group > Activity Log

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-10 13-05-01.png" alt=""><figcaption></figcaption></figure>
