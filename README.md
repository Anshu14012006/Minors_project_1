# Decentralized Book Rental DApp 

A trustless, Ethereum-based book rental platform that enables secure and transparent book lending using smart contracts.
Made by Anshul Garg, Shreyas kale, Maanas, Abinash Acharya, Ajay Sonawani, Shreyash Singh

## Features

This DApp allows:

- **Owners** to list books/items for rent with a daily rental price and refundable deposit.
- **Renters** to borrow items by paying the deposit and rental fee via a smart contract.
- **Smart Contracts** to securely hold deposits, penalize late returns, and refund renters appropriately.

## Technology Stack

- **Blockchain**: Ethereum
- **Smart Contracts**: Solidity
- **Testing Framework**: Truffle & Ganache
- **Frontend**: React.js
- **Web3 Integration**: Web3.js
- **Security**: OpenZeppelin contracts

## Prerequisites

Before you begin, ensure you have the following installed:
- [Node.js](https://nodejs.org/) (v20.x or later)
- [npm](https://www.npmjs.com/) (usually comes with Node.js)
- [Truffle](https://www.trufflesuite.com/truffle) (`npm install -g truffle`)
- [Ganache](https://www.trufflesuite.com/ganache) (for local blockchain testing)
- [MetaMask](https://metamask.io/) browser extension

## Setup & Installation

### 1. Clone the repository


### 2. Install dependencies



### 3. Start Ganache

- Launch Ganache application or CLI
- Create a new workspace (GUI) or start Ganache CLI:
  ```bash
  ganache-cli
  ```
- Ensure it's running on port `8545 or 7545` with network ID `5777 or 1377` and update the truffle.config file

### 4. Configure MetaMask

- Open MetaMask in your browser
- Add a new network:
  - Network Name: `Ganache`
  - New RPC URL: `http://127.0.0.1:8545 or 7545`
  - Chain ID: `5777 or 1377`
  - Currency Symbol: `ETH`
- Import an account from Ganache:
  - Copy one of the private keys from Ganache
  - In MetaMask, click "Import Account" and paste the private key

### 5. Compile and deploy smart contracts

```bash
# Compile contracts
truffle compile

# Deploy to local Ganache network
truffle migrate --reset
```
and update the BookRental.json file by copying it from the build folder.
### 6. Start React frontend

```bash
cd client

# Start the React development server
npm start
```

The application should now be running at [http://localhost:3000](http://localhost:3000)

## Project Structure

```
Project_1/
├── contracts/
│   └── BookRental.sol
├── migrations/
│   ├── 2_deploy_book_rental.js
├── test/
│   └── BookRental.test.js
├── client/
│   ├── public/
│   │   ├── index.html
│   │   ├── favicon.ico
│   │   └── manifest.json
│   ├── src/
|   |    ├──component/
│   │        ├──ListingPage.js
│   │        ├──Marketplace.js
│   │        ├──MyListings.js
│   │        ├──MyRentals.js
│   │   ├── App.js
│   │   ├── App.css
│   │   ├── index.js
│   │   ├── index.css
│   │   └── contracts/
│   │       └── BookRental.json (generated after build)
│   ├── package.json
│   └── README.md
├── truffle-config.js
├── package.json
└── README.md
```

## Smart Contract Overview

The `DecentralizedLottery.sol` contract includes:
- `listItem(title, dailyPrice, deposit)`  
  Allows owners to list books with a refundable deposit and a daily rental rate.

- `rentItem(bookId)`  
  Renter pays `deposit + 1 day's rent`, locking the item.

- `returnItem(bookId)`  
  Calculates rent duration, deducts fee, and refunds remaining deposit.


## Running Tests

```bash
# Navigate to truffle directory
cd truffle

# Run all tests
truffle test

# Run specific test file
truffle test ./test/BookRental.test.js
```


---

## ✨ Features

### 📖 For Book Owners
- List books with:
  - Title
  - Daily rental price
  - Refundable deposit
- View and manage current listings

### 📚 For Renters
- Browse available books
- Rent a book by paying deposit + 1 day rent
- Return books and get refund (minus rental fees)

### 🔐 Smart Contract Automation
- Holds deposits during rental
- Calculates refunds based on rental duration
- Penalizes late returns
- Prevents double rentals
- Emits events: `ItemListed`, `ItemRented`, `ItemReturned`

---

## Deployment to Public Networks

To deploy to Ethereum testnets or mainnet:

1. Update `truffle-config.js` with network configuration
2. Create `.env` file with provider URLs and private keys (use `.env.example` as template)
3. Run:
   ```bash
   truffle migrate --network rinkeby  # or other network name
   ```

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request
