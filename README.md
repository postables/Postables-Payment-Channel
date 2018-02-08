# Postables-Payment-Channel (WIP) --- DEVELOP

# Introduction

Postables Payment Channels is a set of payment channel contract whichs can be reused across multiple different transactions, and parties. Currently payment channels are limited to two participating entities. It is still very much so a work in progress and will be improved over time to include my currently closed-source EVM bridge to enable payment channels across side-chain

# Roadmap ()

1) Introduce the ability for rolling over daily incremental withdrawals
2) Introduce re-usable channels
3) Introduce channel factories to allow  for the existence of multiple PostableHubs (ChannelsV2.sol), each being owned by a single entity, so that each Hub could be used by a business to pay a particular department and so on.
4) Introduce Postables-Bridge to allow for payment channels between mainnet and other EVM chains (side chains)
	> Use PPCT (Postables Payment Channel Tokens) as the collateral mechanism (or ether, design is open at time point)
5) Add web3 desktop or browser Dapp for ease of  use

# Contribution guides:
TO DO


# Bugs and Fixes:

## Improper  address returned from signature verification
```
>>> private
b'\xd8Y\xe3T\xb8\x15\xaaJ\xe6i\xaf\xf9\x02\x8a\xbf\x89#\xf9D\x03\xdd\tc\xf2\xed\xc3\x9eQ\r\x98\xb7|'
>>> signature = w3.eth.account.sign(message_text="hello", private_key=private) 

AttributeDict({'message': HexBytes('0x68656c6c6f'), 'messageHash': HexBytes('0x50b2c43fd39106bafbba0da34fc430e1f91e3c96ea2acee2bc34119f92b37750'), 'r': 53665784189267139251820747046956462498355115993943239404465477346598658281299, 's': 6629064374810355767282561830725699037469490635953226814818888019755260187756, 'v': 27, 'signature': HexBytes('0x76a5c1e7f682df3375a2bdd6f72ad2171b0cf826fc8a8a3209c33a4e57e88f530ea7eadf8603ba2c4a5c5006571be7665020812aa7e403a614587cfe7a18146c1b')})
>>> h = Web3.toHex(signature.messageHash)
>>> v = signature.v
>>> r = Web3.toHex(signature.r)
>>> s = Web3.toHex(signature.s)
>>> h
'0x50b2c43fd39106bafbba0da34fc430e1f91e3c96ea2acee2bc34119f92b37750'
>>> v
27
>>> r
'0x76a5c1e7f682df3375a2bdd6f72ad2171b0cf826fc8a8a3209c33a4e57e88f53'
>>> s
'0xea7eadf8603ba2c4a5c5006571be7665020812aa7e403a614587cfe7a18146c'
>>> Web3.toHex(Web3.toBytes(signature.s))
'0x0ea7eadf8603ba2c4a5c5006571be7665020812aa7e403a614587cfe7a18146c' (returns the correct address)
```
