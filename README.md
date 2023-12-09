# betting-system
This is the betting smart contract for VEX.

<br />

# Quickstart

1. Make sure you have installed [rust](https://rust.org/)
2. Install the [`NEAR CLI`](https://github.com/near/near-cli#setup)

<br />

## 1. Start the contract
By running the below code the contract will be compiled, deployed and then the frontend launched.

```bash
chmod +x magic.sh
./magic.sh
```

<br />

## 2. Interact with the contract via the CLI 

Check the dev account the contract is deployed on
```bash
cat ./contract/neardev/dev-account
# e.g. dev-1659899566943-21539992274727
```

Below are some example commands to interact with the contract:

```bash
npx near-cli <contract-account> create_match '{"team_1": "G2", "team_2": "FURIA", "in_odds_1": 1.2, "in_odds_2": 1.6, "date": "25/07/2023"}' --accountId <contract-account>
npx near-cli call <contract-account> end_betting '{"match_id": "G2-FURIA-25/07/2023"}' --accountId <contract-account>
npx near-cli call <contract-account> finish_match '{"match_id": "G2-FURIA-25/07/2023", "winning_team": "FURIA"}' --accountId <contract-account>
npx near-cli call <contract-account> return_funds '{"match_id": "G2-FURIA-25/07/2023", "state": "Future"}' --accountId <contract-account> --gas 300000000000000 
npx near-cli view <contract-account> view_future_matches '{"match_id": "all"}'
npx near-cli view <contract-account> view_bets '{"match_id": "G2-FURIA-25/07/2023", "name": "all"}'
npx near-cli view <contract-account> view_potential_winnings '{"match_id": "G2-FURIA-25/07/2023", "team": "FURIA", "bet_amount": "2"}'
npx near-cli call cusd.fakes.testnet ft_transfer_call '{"receiver_id": "<contract-account>", "amount": "2000000000000000000000000", "msg": "{\"match_id\": \"G2-FURIA-25/07/2023\", \"decision\": \"G2\"}"}' --accountId <caller-account> --depositYocto 1 --gas 300000000000000
```

<br />
