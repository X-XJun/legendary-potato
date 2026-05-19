## Initial setup

```
npm init -y

npm install --save-dev hardhat@^2.26.3

npx hardhat init

npx hardhat --version
```

![](attachment/e15cdfa19fc311fa24b46fd9d4179b2a.png)

![](attachment/ae0b87239a7f434af2ca481330630873.png)

---

### Read and test default lock contract

Copy and throw the code to remix ide. 

```
contracts/Lock.sol
```

https://www.epochconverter.com/

```
    //Add the following function to the lock contract
    function getCurrentTime() public view returns(uint256){
        uint256 currentTime = block.timestamp;
        return currentTime;
    }
```

---

### Read and run test file

```
/test/Lock.ts

//Command to run the test file
npx hardhat test
```

---

<div style="page-break-after: always;"></div>

### Run hardhat blockchain

```
//Command
npx hardhat node
```

![](attachment/62e674769913e9f24d6f3e867bc310b7.png)

Notes: port conflict

```
//U need to kill process that use the port

//In powershell
netstat -ano | findstr :8545
taskkill /PID <process Id> /F

//In linux
lsof -i :8545
kill [process id]
```

---

### Deploy smart contract

```
//Add the following code to hardhat configuration file -- hardhat.config.ts

  networks: {
    localhost: {
      chainId: 31337,
      url: 'http://127.0.0.1:8545',
    }
  }


//Command to deploy
npx hardhat ignition deploy ./ignition/modules/Lock.ts --reset --network localhost
```

#### Questions

1. How do I get the chainId? (Google search or hardhat documentation)
2. How do I get the url? (Over the console)

---

<div style="page-break-after: always;"></div>

### Automate command in short form

```
//Modify package.json scripts section

npm run deploy
npx hardhat ignition deploy ./ignition/modules/Lock.ts --reset --network localhost

npm run test
npx hardhat test

npm run compile
npx hardhat compile
```

Final Result

![](attachment/1c4ce7dde594441ee3d196bc83d47957.png)

<div style="page-break-after: always;"></div>

---

<div style="page-break-after: always;"></div>

### Connect metamask to hardhat

#### Add Network

![](attachment/41d284eaecde9e505edca9eb6dcb2267.png)

![](attachment/38f3d7afa57ed94601f866b209c155ea.png)

#### Delete network

![](attachment/6685168cf5c35e61f1fa1163c17d853f.png)

<div style="page-break-after: always;"></div>

#### Add Account

![](attachment/2f3c4d7fbe69f6520e74fef2cbb4b25c.png)

![](attachment/4578601b59a5f5a4a52a9e5d1dd4a722.png)

![](attachment/54046ede52f9962956ea2d408b49c434.png)

<div style="page-break-after: always;"></div>

#### Test Sending ETH from account 3 to account 2

![](attachment/97f6898b1fcffc2629d9acb6372cab23.png)

---

### Exercises

1. Try to setup hardhat from scratch again by yourself. 
2. Copy any previous contract from the Remix Ide and deploy it to blockchain using Hardhat framework. 
