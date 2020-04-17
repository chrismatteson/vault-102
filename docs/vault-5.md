name: chapter-5
class: title, shelf, no-footer, fullbleed
background-image: url(https://hashicorp.github.io/field-workshops-assets/assets/bkgs/HashiCorp-Title-bkg.jpeg)
count: false

# Chapter 5
## Other Items

![:scale 15%](https://hashicorp.github.io/field-workshops-assets/assets/logos/logo_vault.png)

???

---
name: vault-agent
# Vault Agent
![:scale 10%](https://hashicorp.github.io/field-workshops-assets/assets/logos/logo_vault.png)

  * Simplify Vault integration
  * Handles Vault Auth, lease renewals
  * Application can simply request secret
  * Templating feature using ConsulTemplate format
  * Caches secrets locally
  * Optimizes Vault performance

???

---
name: vault-agent-lab
layout: false
# Vault Agent Lab
https://www.katacoda.com/hashicorp/scenarios/vault-agent

---
name: identites
layout: false
# Identities
  * Entity's are used for Vault Enterprise Licensing
  * Should track to value which users get from Vault

???

---
name: identites-lab
layout: false
# Identities Lab
https://www.katacoda.com/hashicorp/scenarios/vault-identity

---
name: response-wrapping
layout: false
# Response Wrapping
  * Used to provide additional layer of security by encrypting data

???

---
name: response-wrapping-lab
layout:false
#Response Wrapping Lab
https://www.katacoda.com/hashicorp/scenarios/vault-cubbyhole

---
name: rotate-encrytion-key
layout: false
# Rotate Encryption Key
  * Transit keys exist on key ring
  * Can be rotated at any time
  * Old date still encrypted with old keys, can still be decrypted
  * Rewrap functionality to update key without exposing data

???

---
name: enterprise-capabilities
layout: false
# Enterprise Capabilities
  * Review hashicorp.com feature list
  * DR and Performance Replication
  * Read only Standbys
  * Namespaces

???
