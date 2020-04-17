name: chapter-8
class: title, shelf, no-footer, fullbleed
background-image: url(https://hashicorp.github.io/field-workshops-assets/assets/bkgs/HashiCorp-Title-bkg.jpeg)
count: false

# Chapter 8    
## Encryption as a Service

![:scale 15%](https://hashicorp.github.io/field-workshops-assets/assets/logos/logo_vault.png)

???

* Chapter 8 introduces Vault's Transit secrets engine which functions as Vault's Encryption-as-a-Service (EaaS).

---
layout: true

.footer[
- Copyright © 2019 HashiCorp
- ![:scale 100%](https://hashicorp.github.io/field-workshops-assets/assets/logos/HashiCorp_Icon_Black.svg)
]

---
name: Vault-Transit-Engine

# Vault Transit Engine - Encryption as a Service
.center[![:scale 80%](images/vault-eaas.webp)]

* Vault's Transit Secrets Engine functions as an Encryption-as-a-Service.
* Developers use it to encrypt and decrypt data stored outside of Vault.

???
* Let's talk about Vault's Encryption-as-a-Service, the Transit secrets engine.
* It provides an encryption API & service that are secure, accessible and easy to implement.
* Instead of forcing developers to learn cryptography, we present them with a familiar API that can be used to encrypt and decrypt data that is stored outside of Vault.

---
name: transit-engine-benefits
# Transit Engine Benefits

* Vault's Transit Engine provides developers a well-architected EaaS API so that they don't have to become encryption or cryptography experts.
* It provides centralized key management.
* It ensures that only approved ciphers and algorithms are used.
* It supports automated key rotation and re-wrapping.
* If an attacker manages to get access to the encrypted data, they will only see ciphertext that is useless without Vault.

???
* There are seveal benefits of using the Transit engine.

---
name: Vault-Transit-Engine-1
# Vault Transit - Example Application

* In the next lab we'll use a web application that uses the Transit engine to encrypt and decrypt data.
* The app will store its encrypted data in the same MySQL database we used in Chapter 7.
* It will also get MySQL credentials from the Database secrets engine we configured in that chapter's lab.
* We'll first run the web app without Vault: No records are encrypted.
* We'll then run it with Vault enabled and see that new records are encrypted.

???
* Discuss the web app we will be using in this chapter's lab.
* Point out that it will use the same MySQL database from chapter 7.
* Point out that it will get its MySQL credentials from the Database secrets engine students set up in chapter 7.
* Indicate that we will first run without Vault and then with it.

---
name: web-app-screenshot
# The Web App
### Here is a screenshot of the Python web app:

.center[![:scale 70%](images/transit_app.png)]

???
* Show the screenshot of the web app.

---
name: web-app-views
# The Web App's Views
###There are two main sections in the application.
1. **Records View**
  * The Records View displays records in plain text, showing what a logged in user would see after any encrypted data is decrypted.

1. **Database View**
  * The Database View displays the raw records in the database, showing what SQL commands would return:

---
name: records-view
# The Web App's Records View
.center[![:scale 90%](images/records_view.png)]

* As we would expect an authorized user is able to see some of the sensitive data because the app has decrypted any encrypted data.

???
* Show the records view of the web app.

---
name: Vault-Transit-Engine-6
# The Add User Screen
* In the lab, you will add new users to the database.
.center[![:scale 60%](images/add_user.png)]

???
* Describe the Add User screen that students will use to add new records to the database.
* Point out again that when Vault is enabled, the records will be encrypted in the database.

---
name: database-record-without-vault
# Record in Database View Without Vault Enabled
* After adding a record in the lab, you will be instructed to click on the  **Database View** menu.
* You should see the exact same data that you entered.
* This means that Personally Identifiable Data (PII) is being stored in plain text in our database records.
* How can we improve this? Let's enable Vault's Transit engine and see.

---
name: encrypted-record
# A Database Record Encrypted by Vault
#### Here is a record that was encrypted by Vault's Transit engine.
.center[![:scale 80%](images/database_view_with_encrypted_record.png)]
* Note that the birth_date and social_security_number are encrypted.
???
* Show a record from the database encrypted by Vault's Transit engine.
* Point out that the birth_date and social_security_number field are encrypted as indicated by their starting with "vault:v1".
* Point out that the "v1" indicates that the first version of the encryption key was used.

---
name: encryption-key-rotation
# Rotating Transit Engine Encryption Keys
* The encryption keys of Vaults Transit Engine can be rotated.
* The newest version of the key is used to encrypt new data
* Older versions of the key can still decrypt old data but cannot decrypt new data.
* When we rotate the encryption keys, apps that use the Transit engine are unaware of any changes.
* Data can also be re-encrypted using the `rewrap` endpoint.

