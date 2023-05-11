---
slug: /reference/sdk.erc20signaturemintable.mint
title: Erc20SignatureMintable.mint() method
hide_title: true
displayed_sidebar: typescript
---

<!-- Do not edit this file. It is automatically generated by API Documenter. -->

# Erc20SignatureMintable.mint() method

Mint tokens from a signature

## Example

```javascript
// see how to craft a payload to sign in the `generate()` documentation
const signedPayload = contract.erc20.signature.generate(payload);

// Use the signed payload to mint the tokens
const tx = contract.erc20.signature.mint(signedPayload);
```

**Signature:**

```typescript
mint(signedPayload: SignedPayload20): Promise<TransactionResult>;
```

## Parameters

| Parameter     | Type                                        | Description                                                                                                                       |
| ------------- | ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| signedPayload | [SignedPayload20](./sdk.signedpayload20.md) | the previously generated payload and signature with [Erc20SignatureMintable.generate()](./sdk.erc20signaturemintable.generate.md) |

**Returns:**

Promise&lt;[TransactionResult](./sdk.transactionresult.md)&gt;

## Remarks

Mint a certain amount of tokens from a previously generated signature.