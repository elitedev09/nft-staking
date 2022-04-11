# Deploy your own version 🛠

- `git clone` the repo 
- Make sure you have `solana-cli` installed, keypair configured, and at least 10 sol on devnet beforehand
- Update path to your keypair in `Anchor.toml` that begins with `wallet =`
- Run `anchor build` to build the programs
- We need to update the program IDs:
    - Run `solana-keygen pubkey ./target/deploy/dragon-keypair.json` - insert the new Bank prog ID in the following locations:
        - `./Anchor.toml`
        - `./programs/dragon/src/lib.rs`
        - `./src/index.ts` (replace dragon_PROG_ID)
    - And `solana-keygen pubkey ./target/deploy/dragon_farm-keypair.json` - insert the new Farm prog ID in the following locations:
        - `./Anchor.toml`
        - `./programs/dragon_farm/src/lib.rs`
        - `./src/index.ts` (replace dragon_farm_PROG_ID)
- Run `anchor build` to build one more time
- Run `anchor deploy --provider.cluster devnet` to deploy to devnet
- Now copy the IDLs into the apps:
    - `cp ./target/idl/dragon.json ./app/dragon/public`
    - `cp ./target/idl/dragon.json ./app/dragon-farm/public`
    - `cp ./target/idl/dragon_farm.json ./app/dragon-farm/public`
- alternatively you can run the script I prepared `./scripts/cp_idl.sh`
- (!) IMPORTANT - run `yarn` inside the root of the repo
- finally start the apps!
    - eg cd into `app/dragon` and run yarn && yarn serve
- don't forget to open Chrome's console with `CMD+SHIFT+I` to get feedback from the app when you click buttons. It currently doesn't have a notifications system

Note that deploying your own version will cost you ~20 SOL.
 
The answer you're looking for is probably there. Pls don't DM with random questions.
 