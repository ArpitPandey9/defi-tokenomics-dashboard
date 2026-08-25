# DeFi Tokenomics Dashboard

Streamlit dashboard for inspecting selected public token and DeFi metrics for AAVE, Uniswap (UNI), and Compound (COMP).

## Current implementation

The dashboard attempts to retrieve:

- current token price, market capitalization, and supply data from CoinGecko
- protocol TVL from DeFiLlama
- historical token prices from CoinGecko, with DeFiLlama and Binance fallback paths
- token-supply and historical-price visualizations when the required data is available

Missing provider data is displayed as unavailable rather than replaced with fabricated values.

## Data-source behavior

Public APIs can rate-limit, change schema, or return incomplete observations. The dashboard therefore uses guarded requests and fallback paths, but it does **not** guarantee that every metric or chart will always be available.

The application caches API responses for five minutes.

## Setup

```bash
git clone https://github.com/ArpitPandey9/defi-tokenomics-dashboard.git
cd defi-tokenomics-dashboard

python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt

streamlit run tokenomics-dashboard.py
```

## Validation

Repository CI installs the declared dependencies, checks dependency consistency, parses the Python source, and verifies that known fabricated fallback values and unsupported employer-specific claims are absent.

CI does not simulate or certify third-party API availability.

## Limitations

This is a public-data research dashboard, not an investment recommendation, production market-data service, or representation of any employer or client.

## License

See `LICENSE`.
