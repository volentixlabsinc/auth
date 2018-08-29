# auth
> An authentication service on the EOS blockchain

The Volentix authentication service (or vauth) authenticates users based on a user's public
key (typically their EOS wallet public active key) and a provided password. These two pieces
of data are hashed together on a client and sent to vauth.

This auth service is the mechanism used by [Verto](https://github.io/Volentix/verto) and
[Ledger-UI](https://github.io/Volentix/ledger-ui) to provide security for operations. A detailed
flow will be coming soon.

## API

### `authenticate(wallet, passwordHash)`

Verify that the user identified by the wallet is in fact the owner of the wallet. The wallet
should be a public key and thus identified by an EOS wallet public active key.

This function returns a [JWT](https://jwt.io/).

#### Params

- `wallet`: Data which uniquely identifies a user's wallet, typically their EOS public active key
- `passwordHash`: the result of an MD5 hash of the wallet and a unique password created by the user

### `createUser(wallet, passwordHash)`

Create a new user with the given information. This call fails if a wallet for this user has already
beend defined.

#### Params

- `wallet`: Data which uniquely identifies a user's wallet, typically their EOS public active key
- `passwordHash`: the result of an MD5 hash of the wallet and a unique password created by the user

### `resetPassword(wallet, oldPasswordHash, newPasswordHash)`

Create a new user with the given information. This call fails if a wallet for this user has already
beend defined.

#### Params

- `wallet`: Data which uniquely identifies a user's wallet, typically their EOS public active key
- `oldPasswordHash`: the result of an MD5 hash of the wallet and the previous password
- `newPasswordHash`: the result of an MD5 hash of the wallet and a new password

