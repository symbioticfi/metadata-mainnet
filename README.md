# **Symbiotic entities metadata repository**

This repository is designed to manage metadata and related resources for decentralized entities, such as vaults, networks, operators, and tokens. 
It provides a standardized structure for organizing and accessing information about these entities. 
By contributing to this repository, you help create a reliable, decentralized knowledge base. After being merged, this 
data will be used in [app.symbiotic.fi]() to provide users with accurate and up-to-date information about various entities in the DeFi ecosystem.

---

## **How to Add a New Entity to the Repository via Pull Requests**

### **Repository Structure**

The repository is organized as follows:

```
repository/
├── vaults/
│   ├── 0x<address>/
│   │   ├── info.json
│   │   └── logo.png (optional)
├── networks/
├── operators/
├── tokens/
```

Each entity is identified by its Ethereum address (`0x...`), and its data is stored in a folder named after the address. Inside this folder, there must be a file `info.json` containing metadata, and optionally, an icon file `logo.png`.

---

### **Steps to Add a New Entity**

1. **Determine the entity type**: Decide whether the entity belongs to `vaults`, `networks`, `operators`, or `tokens`.
2. **Create a new folder**: 
   - Navigate to the appropriate directory for the entity type.
   - Create a folder named after the Ethereum address (e.g., `0x1234567890abcdef1234567890abcdef12345678`).
3. **Add the `info.json` file**:
   - Include metadata in the specified format (see below).
4. **(Optional) Add an icon file**:
   - If available, include a `logo.png` file with the entity’s logo.

---

### **File Format: `info.json`**

The `info.json` file must follow this structure:

#### **Required Fields**
- `name` (string): The name of the entity.
- `description` (string): A brief description of the entity.
- `tags` (array of strings): Tags categorizing the entity.
- `links` (array of objects): External links related to the entity.

#### **Optional Fields (for tokens)**
- `cmcId` (string): The CoinMarketCap ID for the token. Used to fetch price of the token in USD.
- `permitName` (string): The `name` field for EIP-2612 support.
- `permitVersion` (string): The `version` field for EIP-2612 support.

#### **Supported `links` Types**
Each link should include:
- `type`: The type of the link. Supported values are:
  - `website`: The official website of the entity.
  - `explorer`: A blockchain explorer link for the entity's Ethereum address or contract.
  - `docs`: Documentation related to the entity.
  - `example`: Example use cases or tutorials.
- `name`: A user-friendly name for the link.
- `url`: The URL of the resource.

#### **Examples**

##### **Token Example**
```json
{
  "name": "USDT",
  "description": "USDT is a stablecoin pegged to the US Dollar, widely used for trading and liquidity in cryptocurrency markets.",
  "tags": ["stablecoin", "usdt"],
  "links": [
    {
      "type": "website",
      "name": "Website",
      "url": "https://tether.to/"
    },
    {
      "type": "explorer",
      "name": "Etherscan",
      "url": "https://etherscan.io/token/0xdac17f958d2ee523a2206206994597c13d831ec7"
    },
    {
      "type": "docs",
      "name": "Tether Documentation",
      "url": "https://docs.tether.to/"
    },
    {
      "type": "example",
      "name": "Integration Guide",
      "url": "https://example.com/usdt-integration"
    }
  ],
  "cmcId": "825",
  "permitName": "USDT Permit Token",
  "permitVersion": "1"
}
```

##### **Vault Example**
```json
{
  "name": "DeFi Vault",
  "description": "A secure vault for decentralized finance.",
  "tags": ["vault", "DeFi"],
  "links": [
    {
      "type": "website",
      "name": "Website",
      "url": "https://example-vault.com/"
    },
    {
      "type": "docs",
      "name": "Vault Documentation",
      "url": "https://example-vault.com/docs"
    }
  ]
}
```

---

### **Icon File: `logo.png` (Optional)**

If you want to include an icon for the entity, follow these guidelines:
- **File Name**: `logo.png`
- **Dimensions**: 256x256 pixels
- **Format**: PNG

Place the `logo.png` file in the same folder as the `info.json` file.

---

### **Validation**

Before submitting your PR, ensure the following:
1. The Ethereum address is valid:
   - It must start with `0x` and be exactly 42 characters long.
2. The `info.json` file is valid:
   - Use a JSON validator, such as [https://jsonlint.com/](https://jsonlint.com/).
3. The `logo.png` file (if included) meets the size requirement of **256x256 pixels**.

---

### **Submitting the Pull Request**

Once your files are added to the repository, create a Pull Request with the following details:
1. **Entity Type**: Specify the type (vault, network, operator, token).
2. **Ethereum Address**: Provide the address of the entity.
3. **Description**: Summarize the entity’s purpose and data.

#### **Example PR Description**
```
Added new token entity: 0x1234567890abcdef1234567890abcdef12345678

- **Name**: USDT
- **Description**: USDT is a stablecoin pegged to the US Dollar, widely used for trading and liquidity in cryptocurrency markets.
- **Tags**: stablecoin, usdt
- **Links**: 
  - [Website](https://tether.to/)
  - [Etherscan](https://etherscan.io/token/0xdac17f958d2ee523a2206206994597c13d831ec7)
  - [Tether Documentation](https://docs.tether.to/)
- **CMC ID**: 825
- **Permit Name**: USDT Permit Token
- **Permit Version**: 1
- **Icon**: Included (256x256 px)
```

---

### **Review and Approval**

Your PR will be reviewed to ensure:
- The `info.json` file has all required fields and valid data.
- The `logo.png` file (if included) meets the requirements.
- The metadata is accurate and well-structured.

After approval, your changes will be merged into the repository. Thank you for your contribution! 🎉

If you have any questions or issues, feel free to reach out to the symbiotic team.
