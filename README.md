# MetaCoin

1.    Create a new directory for your Truffle project:

 >   mkdir MetaCoin
 >   cd MetaCoin

2.    Download ("unbox") the MetaCoin box:

 >   truffle unbox metacoin

    Note: You can use the truffle unbox <box-name> command to download any of the other Truffle Boxes.

To create a bare Truffle project with no smart contracts included, use truffle init.

 > truffle init

Once this operation is completed, you'll now have a project structure with the following items:

    contracts/: Directory for Solidity contracts
    migrations/: Directory for scriptable deployment files
    test/: Directory for test files for testing your application and contracts
    truffle.js: Truffle configuration file

  
3. Testing

    On a terminal, run the Solidity test:

>    truffle test ./test/TestMetacoin.sol

    Run the JavaScript test:

>    truffle test ./test/metacoin.js


4. Compiling

>    truffle compile


 
5. Migrating with Truffle Develop

Note: To use Ganache, please skip to the next section.

You can create this blockchain and interact with it using Truffle Develop.
Run Truffle Develop:

 >   truffle develop

You will see the following information:

 >   Truffle Develop started at http://127.0.0.1:9545/
 >   truffle(development)>
 >   migrate

 
6. Alternative: Migrating with Ganache

-    Download and install Ganache.

-    Open truffle.js in a text editor. Replace the content with the following:

    module.exports = {
      networks: {
        development: {
          host: "127.0.0.1",
          port: 7545,
          network_id: "*"
        }
      }
    };

    This will allow a connection using Ganache's default connection parameters.

    On the terminal, migrate the contract to the blockchain created by Ganache:

 >   truffle migrate

 >    truffle console

    You will see the following prompt:

 >   truffle(development)>

 
7. Interacting with the contract

Check the metacoin balance of the account that deployed the contract:

 >   MetaCoin.deployed().then(function(instance){return instance.getBalance(web3.eth.accounts[0]);}).then(function(value){return value.toNumber()});

See how much ether that balance is worth (and note that the contract defines a metacoin to be worth 2 ether):

 >   MetaCoin.deployed().then(function(instance){return instance.getBalanceInEth(web3.eth.accounts[0]);}).then(function(value){return value.toNumber()});

Transfer some metacoin from one account to another:

 >   MetaCoin.deployed().then(function(instance){return instance.sendCoin(web3.eth.accounts[1], 500);});

Check the balance of the account that received the metacoin:

  >  MetaCoin.deployed().then(function(instance){return instance.getBalance(web3.eth.accounts[1]);}).then(function(value){return value.toNumber()});

Check the balance of the account that sent the metacoin:

 >   MetaCoin.deployed().then(function(instance){return instance.getBalance(web3.eth.accounts[0]);}).then(function(value){return value.toNumber()});



Tutorial: https://truffleframework.com/docs/getting_started/project
