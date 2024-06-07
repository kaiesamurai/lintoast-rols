
# Lintoast — Revolutionizing Digital Ownership with Generative NFTs

## Inspiration

"Lintoast" is born from the vision of leveraging blockchain technology to redefine digital ownership. We saw an opportunity to create a platform where unique digital assets can be minted, transferred, and claimed across different chains, showcasing the potential of the Linera blockchain ecosystem.

## What it does

"Lintoast" enables the creation, management, and cross-chain transfer of non-fungible tokens (NFTs). Key features include:

- **Minting NFTs:** Create unique digital assets.
- **Transferring NFTs:** Move NFTs between accounts on the same or different chains.
- **Claiming NFTs:** Transfer ownership of NFTs across chains using cross-chain messages.

## How we built it

Built using the Linera framework and Rust programming language, "Lintoast" combines robust backend capabilities with a seamless frontend experience. Key steps included:

1. **Setup Linera Network:** Initialize the local network and configure wallet and storage.
2. **Compile Application:** Build the application’s WebAssembly binaries.
3. **Publish Bytecode:** Deploy the application bytecode to the Linera chain.
4. **Mint and Manage NFTs:** Use the application to create, transfer, and claim NFTs.

## Challenges we ran into

Building "Lintoast" involved overcoming several challenges:

- **Learning Curve:** Mastering Rust’s memory management and concurrency models.
- **API Integration:** Handling rate limits and errors during API integration.
- **Security:** Implementing robust authentication and encryption mechanisms.
- **Deployment:** Managing the unique compilation model of Rust-based applications.

## Accomplishments that we're proud of

Despite the challenges, we achieved:

- **Advanced Security:** Ensured the safety of user data and digital assets.
- **Seamless User Experience:** Developed an intuitive interface with positive feedback.
- **Cross-Chain Transfers:** Enabled smooth transfer and claiming of NFTs across chains.
- **Real-Time Data:** Integrated real-time market data and updates.

## What we learned

The development process provided valuable insights:

- **Rust Expertise:** Deepened our understanding of Rust’s programming paradigms.
- **Asynchronous Programming:** Improved handling of asynchronous operations and API integrations.
- **Cybersecurity:** Enhanced our knowledge of security best practices.
- **Deployment Strategies:** Learned about deploying Rust-based applications.
- **Collaboration:** Reinforced the importance of teamwork and iterative development.

## What's next for Lintoast

Future plans for "Lintoast" include:

- **Expand Cryptocurrency Support:** Add more cryptocurrencies.
- **Advanced Trading Features:** Introduce sophisticated trading tools and DeFi integrations.
- **Mobile Application:** Develop a mobile app for on-the-go NFT management.
- **Community Engagement:** Enhance social features for a vibrant community.
- **Educational Resources:** Expand content to educate users about NFTs and blockchain technology.
- **Strategic Partnerships:** Form alliances with other blockchain projects and ensure regulatory compliance.

## Getting Started

### Prerequisites

Ensure you have the model and tokenizer locally:

```bash
wget -O model.bin -c https://huggingface.co/karpathy/tinyllamas/resolve/main/stories42M.bin
wget -c https://huggingface.co/spaces/lmz/candle-llama2/resolve/main/tokenizer.json
```

Run the Python server to serve models locally:

```bash
python3 -m http.server 10001 &
```

### Setup

Set up your local network and compile the application:

```bash
export PATH="$PWD/target/debug:$PATH"
source /dev/stdin <<<"$(linera net helper 2>/dev/null)"
linera_spawn_and_read_wallet_variables linera net up --testing-prng-seed 37
```

Compile the application WebAssembly binaries and publish the bytecode:

```bash
(cd examples/gen-nft && cargo build --release)
BYTECODE_ID=$(linera publish-bytecode \
    examples/target/wasm32-unknown-unknown/release/gen_nft_{contract,service}.wasm)
```

### Creating an NFT

Retrieve the application ID and create NFTs:

```bash
APP_ID=$(linera create-application $BYTECODE_ID)
```

### Using the NFT Application

Start the node service and access the web frontend:

```bash
PORT=8080
linera service --port $PORT &
cd examples/gen-nft/web-frontend
npm install --no-save
BROWSER=none npm start &
```

Access the application via the provided URLs:

```bash
echo "http://localhost:3000/$CHAIN_1?app=$APP_ID&owner=$OWNER_1&port=$PORT"
echo "http://localhost:3000/$CHAIN_1?app=$APP_ID&owner=$OWNER_2&port=$PORT"
```

## Built With

- **Linera**
- **Rust**

Explore the world of generative NFTs with "Lintoast" and experience the future of digital asset management!
