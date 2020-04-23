# Blockchain


Create new directory in repository:
(base) Jeans-MacBook-Air:Blockchain jean$ mkdir geth

Running Puppeth:
(base) Jeans-MacBook-Air:Blockchain jean$ puppeth
+-----------------------------------------------------------+
| Welcome to puppeth, your Ethereum private network manager |
|                                                           |
| This tool lets you create a new Ethereum network down to  |
| the genesis block, bootnodes, miners and ethstats servers |
| without the hassle that it would normally entail.         |
|                                                           |
| Puppeth uses SSH to dial in to remote servers, and builds |
| its network components out of Docker containers using the |
| docker-compose toolset.                                   |
+-----------------------------------------------------------+
Please specify a network name to administer (no spaces, hyphens or capital letters please)
> gandalf

Sweet, you can set this via --network=gandalf next time!

INFO [04-23|15:30:32.839] Administering Ethereum network           name=gandalf
WARN [04-23|15:30:32.840] No previous configurations found         path=/Users/jean/.puppeth/gandalf

What would you like to do? (default = stats)
 1. Show network stats
 2. Configure new genesis
 3. Track new remote server
 4. Deploy network components
> 2

What would you like to do? (default = create)
 1. Create new genesis from scratch
 2. Import already existing genesis
> 1

Which consensus engine to use? (default = clique)
 1. Ethash - proof-of-work
 2. Clique - proof-of-authority
> 2

How many seconds should blocks take? (default = 15)
> 

Which accounts are allowed to seal? (mandatory at least one)
> 0x
> 0x
> 0x118a8ad7595103F006f030733B7518ED12055c48                                      
> 0x

Which accounts should be pre-funded? (advisable at least one)
> 0x118a8ad7595103F006f030733B7518ED12055c48
> 0x

Should the precompile-addresses (0x1 .. 0xff) be pre-funded with 1 wei? (advisable yes)
> yes

Specify your chain/network ID if you want an explicit one (default = random)
> 
INFO [04-23|15:35:18.777] Configured new genesis block 

What would you like to do? (default = stats)
 1. Show network stats
 2. Manage existing genesis
 3. Track new remote server
 4. Deploy network components
> 2

 1. Modify existing configurations
 2. Export genesis configurations
 3. Remove genesis configuration
> 2

Which folder to save the genesis specs into? (default = current)
  Will create gandalf.json, gandalf-aleth.json, gandalf-harmony.json, gandalf-parity.json
> 
INFO [04-23|15:57:35.499] Saved native genesis chain spec          path=gandalf.json
ERROR[04-23|15:57:35.499] Failed to create Aleth chain spec        err="unsupported consensus engine"
ERROR[04-23|15:57:35.499] Failed to create Parity chain spec       err="unsupported consensus engine"
INFO [04-2


# Nodes 

# Creating Node 1 And Node 2

(base) Jeans-MacBook-Air:Blockchain jean$ ls
README.md		gandalf-harmony.json	gandalf.json		geth
(base) Jeans-MacBook-Air:Blockchain jean$ geth account new --datadir node1
INFO [04-23|16:08:56.744] Maximum peer count                       ETH=50 LES=0 total=50
Your new account is locked with a password. Please give a password. Do not forget this password.
Password: 
Repeat password: 

Your new key was generated

Public address of the key:   0xFEFfE762DCECb80a6D563809DB2941c420D63819
Path of the secret key file: node1/keystore/UTC--2020-04-23T21-09-04.105585000Z--feffe762dcecb80a6d563809db2941c420d63819

- You can share your public address with anyone. Others need it to interact with you.
- You must NEVER share the secret key with anyone! The key controls access to your funds!
- You must BACKUP your key file! Without the key, it's impossible to access account funds!
- You must REMEMBER your password! Without the password, it's impossible to decrypt the key!

(base) Jeans-MacBook-Air:Blockchain jean$ geth account new --datadir node2
INFO [04-23|16:10:39.729] Maximum peer count                       ETH=50 LES=0 total=50
Your new account is locked with a password. Please give a password. Do not forget this password.
Password: 
Repeat password: 

Your new key was generated

Public address of the key:   0x5a9464D83517592f28722F9d516e5A7C7CfC4985
Path of the secret key file: node2/keystore/UTC--2020-04-23T21-10-44.475608000Z--5a9464d83517592f28722f9d516e5a7c7cfc4985

- You can share your public address with anyone. Others need it to interact with you.
- You must NEVER share the secret key with anyone! The key controls access to your funds!
- You must BACKUP your key file! Without the key, it's impossible to access account funds!
- You must REMEMBER your password! Without the password, it's impossible to decrypt the key!

# Initialise node 1 & node 2

(base) Jeans-MacBook-Air:Blockchain jean$ geth init gandalf.json --datadir node1
INFO [04-23|16:15:41.110] Maximum peer count                       ETH=50 LES=0 total=50
INFO [04-23|16:15:41.145] Allocated cache and file handles         database=/Users/jean/Documents/Homework/Blockchain/node1/geth/chaindata cache=16.00MiB handles=16
INFO [04-23|16:15:41.192] Writing custom genesis block 
INFO [04-23|16:15:41.214] Persisted trie from memory database      nodes=355 size=50.43KiB time=3.417522ms gcnodes=0 gcsize=0.00B gctime=0s livenodes=1 livesize=0.00B
INFO [04-23|16:15:41.217] Successfully wrote genesis state         database=chaindata hash=114544…e227e7
INFO [04-23|16:15:41.217] Allocated cache and file handles         database=/Users/jean/Documents/Homework/Blockchain/node1/geth/lightchaindata cache=16.00MiB handles=16
INFO [04-23|16:15:41.254] Writing custom genesis block 
INFO [04-23|16:15:41.266] Persisted trie from memory database      nodes=355 size=50.43KiB time=1.288105ms gcnodes=0 gcsize=0.00B gctime=0s livenodes=1 livesize=0.00B
INFO [04-23|16:15:41.267] Successfully wrote genesis state         database=lightchaindata hash=114544…e227e7
(base) Jeans-MacBook-Air:Blockchain jean$ get init gandalf.json --datadir node2
-bash: get: command not found
(base) Jeans-MacBook-Air:Blockchain jean$ geth init gandal.json --datadir node2
Fatal: Failed to read genesis file: open gandal.json: no such file or directory
(base) Jeans-MacBook-Air:Blockchain jean$ geth init gandalf.json --datadir node2
INFO [04-23|16:17:44.019] Maximum peer count                       ETH=50 LES=0 total=50
INFO [04-23|16:17:44.033] Allocated cache and file handles         database=/Users/jean/Documents/Homework/Blockchain/node2/geth/chaindata cache=16.00MiB handles=16
INFO [04-23|16:17:44.075] Writing custom genesis block 
INFO [04-23|16:17:44.084] Persisted trie from memory database      nodes=355 size=50.43KiB time=1.53501ms gcnodes=0 gcsize=0.00B gctime=0s livenodes=1 livesize=0.00B
INFO [04-23|16:17:44.085] Successfully wrote genesis state         database=chaindata hash=114544…e227e7
INFO [04-23|16:17:44.085] Allocated cache and file handles         database=/Users/jean/Documents/Homework/Blockchain/node2/geth/lightchaindata cache=16.00MiB handles=16
INFO [04-23|16:17:44.125] Writing custom genesis block 
INFO [04-23|16:17:44.131] Persisted trie from memory database      nodes=355 size=50.43KiB time=1.416889ms gcnodes=0 gcsize=0.00B gctime=0s livenodes=1 livesize=0.00B
INFO [04-23|16:17:44.132] Successfully wrote genesis state         database=lightchaindata hash=114544…e227e7

# Once both nodes are running , I open up My Crypto and change the network ==> add custom node  my newtwork name "gandalf"

# once linked we can see that the account balance will change from $ 0 to $ 904, 625 ....

# this concludes that My crypto is connected to my network.
