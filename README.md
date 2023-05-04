# Relevant Multisigs

| Multisig | Address |
| -------- | ------- |
| 0x245cc372C84B3645Bf0Ffe6538620B04a217988B | Treasury Multisig |

# Understanding Roles

### Relevant Contracts
1. **ROLES.v1.sol**
	- Module that stores the active system roles
2. **RolesAdmin.sol**
	- Policy that has the ability to grant and revoke roles from `ROLES.v1.sol`
	- Only the `admin` can grant/revoke roles and propose a  `newAdmin` (2-step process).
	- `admin`: 0x245cc372C84B3645Bf0Ffe6538620B04a217988B (Treasury Multisig)