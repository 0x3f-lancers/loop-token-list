# Loop Token List Repository

Welcome to the Loop Token List Repository. This repository maintains a curated list of tokens used across our platform. Below, you will find the token format, guidelines on how to submit a pull request (PR) to add your token, and details on how to use this list effectively.

## Table of Contents

1. [Token List Format](#token-list-format)
2. [How to Add Your Token](#how-to-add-your-token)
3. [Submitting a Pull Request (PR)](#submitting-a-pull-request-pr)
4. [Usage Guidelines](#usage-guidelines)
5. [Maintainers](#maintainers)

### Token List Format

Each token entry in the list follows the JSON format below. Ensure your token entry strictly follows this schema to avoid validation failures during review.

```json
{
  "symbol": "TOKEN",
  "name": "Token Name",
  "address": "0x1234567890abcdef1234567890abcdef12345678",
  "decimals": 18,
  "chainId": 1,
  "sellFeeBps": 0,
  "buyFeeBps": 0,
  "isNative": true,
  "isToken": false,
  "logoURI": "https://path-to-your-logo/logo.png",
  "socials": {
    "twitter": "https://twitter.com/yourtoken",
    "telegram": "https://t.me/yourtoken"
  },
  "coingeckoId": "your-token-id"
}
```

#### Explanation of Fields

| **Field**     | **Type** | **Description**                                                                                | **Required** |
| ------------- | -------- | ---------------------------------------------------------------------------------------------- | ------------ |
| `symbol`      | String   | The token's ticker symbol (e.g., `ETH`, `BEE`).                                                | Yes          |
| `name`        | String   | The full name of the token.                                                                    | Yes          |
| `address`     | String   | The token's **contract address** on the blockchain. Must follow Ethereum-style `0x...` format. | Yes          |
| `decimals`    | Number   | Number of decimals the token supports (typically between 0 and 18).                            | Yes          |
| `chainId`     | Number   | ID of the blockchain where the token resides (e.g., `1` for Ethereum, `56` for BNB Chain).     | Yes          |
| `sellFeeBps`  | Number   | The sell fee in basis points (bps).                                                            | No           |
| `buyFeeBps`   | Number   | The buy fee in basis points (bps).                                                             | No           |
| `isNative`    | Boolean  | Indicates if the token is a native token of the blockchain.                                    | No           |
| `isToken`     | Boolean  | Indicates if the entry is a token.                                                             | No           |
| `logoURI`     | String   | A public URL to the token's logo image. Must be **PNG** or **SVG**.                            | Yes          |
| `socials`     | Object   | Links to the token’s social profiles (Twitter, Telegram, etc.).                                | Optional     |
| `coingeckoId` | String   | The token's ID on CoinGecko.                                                                   | Optional     |

### How to Add Your Token

To list your token on our platform, follow these steps carefully:

1. Fork this repository by clicking the “Fork” button in the top-right corner.
2. Clone your forked repository to your local machine:

   ```bash
   git clone https://github.com/0x3f-lancers/loop-token-list.git
   cd loop-token-list/src
   ```

3. Add your token entry to the `main-tokens.json` file following the [Token List Format](#token-list-format).
4. Commit your changes:

   ```bash
   git add tokens.json
   git commit -m "Add TOKEN_NAME to the token list"
   ```

5. Push your changes:

   ```bash
   git push origin main
   ```

6. Open a Pull Request (PR) by visiting your forked repository on GitHub and clicking the “Compare & Pull Request” button.

### Submitting a Pull Request (PR)

When submitting a PR, ensure you follow these guidelines to avoid delays in approval:

1. **Follow the token format strictly**: Invalid addresses, empty fields, or missing fields will result in rejection.
2. **Provide accurate information**: Ensure all social media links, addresses, and decimals are correct.
3. **Attach your token logo**: The logo should be a public URL accessible over the internet. Avoid using IPFS or private URLs.
4. **Logo Requirements**: The token logo should be 24x24 pixels or 32x32 pixels in size for optimal display.
5. **Review your PR summary**: Provide a clear description of the token you’re adding.

### Alternative Method 1

1. **Create an Issue**: If you’re unsure about the token format or need help, create an issue in this repository.

2. **Request Token Addition**: Provide the token details in the issue description, and we’ll add it to the list for you.

3. **Review and Approval**: Once your token is added, you can review the changes and suggest any modifications if needed.

### Alternative Method 2

1. **Contact the Maintainers**: If you’re unable to create a PR or issue, contact the repository maintainers directly through [telegram](https://t.me/busybeeloop)

2. **Provide Token Details**: Share the token details with the maintainers, and they will add the token to the list for you.

3. **Review and Approval**: You can review the changes and suggest any modifications if needed.

### Usage Guidelines

The `main-tokens.json` file can be used to fetch token information in your frontend applications. Here’s a sample API request to retrieve the token list:

```bash
curl -X GET https://raw.githubusercontent.com/0x3f-lancers/loop-token-list/main/src/main-tokens.json
```

You can also integrate the list in your frontend apps:

```javascript
async function fetchTokenList() {
  const response = await fetch(
    "https://raw.githubusercontent.com/0x3f-lancers/loop-token-list/main/src/main-tokens.json"
  );
  const tokens = await response.json();
  console.log(tokens);
}

fetchTokenList();
```

### Token Validation

We run manual and automated checks on the token list to ensure correctness. If your PR fails validation, you will receive feedback on the changes needed.

#### Common Reasons for Rejection:

- Invalid contract address format (must follow `0x...` format).
- Incorrect or missing decimals.
- Social media URLs that don’t work.
- Using a non-public URL for the token logo.

### Maintainers

If you have any questions or need help, feel free to contact the repository maintainers:

- [**0xlancersT**](https://lancers.technology)
- [**BusyBee**](https://busybee.bond)

### License

This repository is licensed under the MIT License.

### Summary

By following this guide, you’ll ensure a smooth token submission process. Please review your changes carefully before submitting a PR to avoid delays. Happy token listing!
