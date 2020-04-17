name: chapter-3
class: title, shelf, no-footer, fullbleed
background-image: url(https://hashicorp.github.io/field-workshops-assets/assets/bkgs/HashiCorp-Title-bkg.jpeg)
count: false

# Chapter 3
## Additional Depth on Tokens

![:scale 15%](https://hashicorp.github.io/field-workshops-assets/assets/logos/logo_vault.png)

???
We will cover additional information on Tokens

---
name: types-of-tokens
# Types of Tokens
![:scale 10%](https://hashicorp.github.io/field-workshops-assets/assets/logos/logo_vault.png)

  * "Regular" Tokens
  * Orphan Tokens
  * Batch Tokens

???

---
name: describe-token-accessors
layout: false
# Describe Token Accessors
  * Unique ID seperate from token for tracking
  * Can be used to revoke or renew token

???

---
name: time-to-live
# Time to Live
  * All tokens except root tokens have TTL
  * Based on policy, tokens can be extended
  * Extending is cheaper operationally than reauthenticating
  * Batch tokens can't be extended, but can be even cheaper operationally

???

---
name: token-lab
# Token Lab
https://www.katacoda.com/hashicorp/scenarios/vault-tokens
