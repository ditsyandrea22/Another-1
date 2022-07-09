# Another-1
# Auto Install
wget -q -O another-1.sh https://raw.githubusercontent.com/ditsyandrea22/Another-1/7275934bc3065eb8bde19411877d918da9e9aac9/another-1.sh && chmod +x another-1.sh && sudo /bin/bash another-1.sh
# after installation
source $HOME/.bash_profile
# validator info
anoned status 2>&1 | jq .ValidatorInfo

anoned status 2>&1 | jq .SyncInfo

anoned status 2>&1 | jq .NodeInfo
# Create your wallet
# Add New Wallet
anoned keys add wallet
# Recover Existing Wallet
anoned keys add wallet --recover
# List All Wallet
anoned keys list
# Check Wallet Balance
anoned q bank balances $(anoned keys show wallet -a)
# Validator
# Create New Validator
anoned tx staking create-validator \
--amount=1000000uan1 \
--pubkey=$(anoned tendermint show-validator) \
--moniker="<YOUR NODENAME>" \
--identity=<YOUR IDENTITY> \
--details="<YOUR DETAILS>" \
--chain-id=anone-testnet-1 \
--commission-rate=0.10 \
--commission-max-rate=0.20 \
--commission-max-change-rate=0.01 \
--min-self-delegation=1 \
--from=wallet \
--fees=2000uan1 \
--gas=auto \
-y
