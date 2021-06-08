# [Vault by HashiCorp](https://www.vaultproject.io/)
Enable the AppRole auth method:
```sh
vault auth enable approle
```
Create polici:
```sh
vault policy write [POLICI_NAME] [POLICI_FILE].hcl
```
Create a named role and add polici:
```sh
vault write auth/approle/role/[ROLE_NAME]  secret_id_ttl=0  token_ttl=0  token_max_tll=0  policies="[POLICI_NAME]"
```
Fetch the RoleID of the AppRole:
```sh
vault read auth/approle/role/[ROLE_NAME]/role-id
```
Get a SecretID issued against the AppRole:
```sh
vault write -f auth/approle/role/[ROLE_NAME]/secret-id
```
Add new Secret:
```sh
vault kv put [WAY_TO_SECRETS] [KEY]=[VALUE]
```
