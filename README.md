# Tradestation Python API

A Python Client library for the TradeStation API V3.

## Table of Contents

- [Overview](#overview)
- [What's in the API](#whats-in-the-api)
- [Requirements](#requirements)
- [API Key & Credentials](#api-key-and-credentials)
- [Installation](#installation)
- [Usage](#usage)
- [Features](#features)
- [Documentation & Resources](#documentation-and-resources)
- [About this Project](#about-this-project)

## Overview

The unofficial Python API client library for TradeStation allows individuals with TradeStation accounts to manage trades, pull historical and real-time data, manage their accounts, create and modify orders all using the Python programming language.

To learn more about the TradeStation API, please refer to the [official documentation](https://developer.tdameritrade.com/apis).

## What's in the API

- Authentication - access tokens, refresh tokens, request authentication.
- Accounts & Trading
- Symbols
- Index
- Orders
- Paper Trading
- Quotes
- Transaction History

## Requirements

The following requirements must be met to use this API:

- A TradeStation account, you'll need your account password and account number to use the API.
- A TradeStation Developer API Key
- A Redirect URI, sometimes called Redirect URL
- Python 3.8 or later.

## API Key and Credentials

Each TradeStation API request requires a TradeStation Developer API Key, a consumer ID, an account password, an account number, and a redirect URI. API Keys, consumer IDs, and redirect URIs are generated from the TradeStation developer portal. To set up and create your TradeStation developer account, please refer to the [official documentation](https://api.tradestation.com/docs/).

Additionally, to authenticate yourself using this library, you will need to provide your account number and password for your main TradeStation account.

**Important:** Your account number, an account password, consumer ID, and API key should be kept secret.

## Installation

```bash
pip install -e .
```

## Usage

This example demonstrates how to login to the API and demonstrates sending a request using the `quotes`, and `stream_bars_start_date` endpoint, using your API key.

```python
# Import the client
from ts.client import TradeStationClient

# Create the Client.
ts_client = TradeStationClient(
    username="USERNAME",
    client_id="CLIENT_ID",
    client_secret="CLIENT_SECRET",  
    redirect_uri="REDIRECT_URI",
    paper_trading="PAPER_TRADING"
)

# Get quotes for Oil Futures.
ts_client.quotes(symbols=['@CL'])

# Stream quotes for Amazon.
ts_client.stream_quotes_changes(symbols=['AMZN'])

# Stream bars for a certain date.
ts_client.stream_bars_start_date(
    symbol='AMZN',
    interval=5,
    unit='Minute',
    start_date='02-25-2020',
    session='USEQPreAndPost'
)
```

## Features

### Authentication Workflow Support

Automatically will handle the authentication workflow for new users, returning users, and users with expired tokens (refresh token or access token).

### Request Validation

For certain requests, in a limited fashion, it will help validate your request when possible. For example, when using the `get_bars` endpoint, it will automatically validate that the market you're requesting data from is one of the valid options.

## Documentation and Resources

- [Overview](https://api.tradestation.com/docs/fundamentals/authentication/auth-overview)
- [Paper Trading](https://api.tradestation.com/docs/fundamentals/sim-vs-live)
- [Authentication](https://api.tradestation.com/docs/fundamentals/authentication/auth-code)

## About this Project

Fork from [tradestation-python-api](https://github.com/areed1192/tradestation-python-api).

