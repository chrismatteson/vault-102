name: chapter-4
class: title, shelf, no-footer, fullbleed
background-image: url(https://hashicorp.github.io/field-workshops-assets/assets/bkgs/HashiCorp-Title-bkg.jpeg)
count: false

# Chapter 4
## Additional Depth on Leases

![:scale 15%](https://hashicorp.github.io/field-workshops-assets/assets/logos/logo_vault.png)

???
We will cover additional information on Tokens

---
name: lease-id
# Lease ID
![:scale 10%](https://hashicorp.github.io/field-workshops-assets/assets/logos/logo_vault.png)

  * Way to track leases
  * Required to renew or revoke
  * Can not be listed from CLI, but can from UI or API
  * Can be revoked with wild card

???

---
name: renew-lease
layout: false
# Renew Lease
  * Configurable in secret engine
  * Operationally cheaper than requesting new secret

???

