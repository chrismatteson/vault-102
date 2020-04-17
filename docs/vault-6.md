---
name: vault-policies
# Vault Policies
* Vault Policies restrict the secrets users and applications have access to.
* Vault follows the practice of least privilege, *denying* access by default.
* Vault administrators must explicity grant users and applications access to specific paths with policy statements.
* In addition to specifying paths, policies also specify a set of capabilities for those paths.
* Policies are written in HashiCorp Configuration Language (HCL).

---
name: vault-policy-example
# A Vault Policy Example
* Here is an example of a Vault policy:
```hcl
# Allow tokens to look up their own properties
path "auth/token/lookup-self" {
    capabilities = ["read"]
}
```
* Note that this policy does not allow tokens to change their own properties.
???
* This policy allows tokens to look up their own properties

---
name: vault-policy-paths-capabilities
# Policy Paths and Capabilities
* The path of a policy maps to a Vault API path.
* The most common capabilities granted are: `create`, `read`, `update`, `delete`, and `list` which correspond to HTTP verbs like POST and GET.
* Two other capabilities do not correspond to HTTP verbs:
  * `sudo` allows access to paths that are root-protected.
  * `deny` denies access to a path and takes precedence over other capabilities.

???
* Explain policy paths and capabilities

---
name: policies-for-lobs
# Configuring Policies for LOBs
* Many organizations organize Vault secrets by line of business (LOB) and department.
* Here's an example policy for line of business A, department 1:

```hcl
path "lob_a/dept_1/*" {
    capabilities = ["read", "list", "create", "delete", "update"]
}
```

* This policy grants all standard capabilities to all secrets mounted under `lob_a/dept_1/` by using the glob character (`*`).

???
* Talk about how many organizations organize Vault secrets by line of business and department.
* Explain the policy including the glob character and that it can only be used at the end of a path.

---
name: vault-policy-commands
# Vault Policy CLI Commands
* Vault policies can be added to a Vault server using Vault's CLI, UI, or API.
* The command to add a policy with the CLI is `vault policy write`.
* Here is a command that creates a policy called "lob-A-dept-1" from the HCL file "lob-A-dept-1-policy.hcl":<br>
`vault policy write lob-A-dept-1 lob-A-dept-1-policy.hcl`
* Here is a command that associates this policy with a Userpass user:<br>
`vault write auth/userpass/users/joe/policies policies=lob-A-dept-1`

???
Describe the most important Vault CLI commands for policies.

