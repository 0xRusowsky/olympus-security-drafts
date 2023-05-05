# Relevant Multisigs
| Multisig | Network | Address | Roles | Setup |
| ------- | -------- | ------- | ------| ------- |
| DAO Multisig | Mainnet | 0x245cc372C84B3645Bf0Ffe6538620B04a217988B | [`admin`, `emergency_restart`] | 4/8 |
| Emergency Multisig| Mainnet  | 0xa8A6ff2606b24F61AFA986381D8991DFcCCd2D55 | [`emergency_shutdown`] | 2/8 |
| Policy Multisig | Mainnet | 0x0cf30dc0d48604A301dF8010cdc028C055336b2E | [] | 3/5 |

# Understanding Roles

### Relevant Contracts
1. **ROLES.v1.sol**
	- Module that stores all the active system roles.
2. **RolesAdmin.sol**
	- Policy that has the ability to grant and revoke roles from `ROLES.v1.sol`
	- Only the `admin` can grant/revoke roles by calling `grantRole()` and `revokeRole()` respectively.
	- Only the `admin` can propose a `newAdmin` by calling `pushNewAdmin()`. On top of that, the `newAdmin` must accept the role by calling `pullNewAdmin()`.
3. **Emergency.sol**
	- Policy that has the ability to shutdown critical system functionalities (`MINTR.v1.sol` and `TRSRY.v1.sol` modules)
	- `emergency_shutdown`: has the ability to shutdown Treasury withdrawals by calling `shutdownWithdrawals()`, Minting capabilities by calling `shutdownMinting()`, or both by calling `shutdown()`. This role is held by the Emergency Multisig, requiring only 2 confirmations out of 8 signers.
	- `emergency_restart`: has the ability to restart Treasury withdrawals by calling `restartWithdrawals()`, Minting capabilities by calling `restartMinting()`, or both by calling `restart()`. This role is held by the DAO Multisig, requiring 4 confirmations out of 8 signers.