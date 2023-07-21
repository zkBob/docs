---
description: Switching library to the full state mode
---

# Attaching a User Account

## <mark style="background-color:green;">Login</mark>

To set the customer's wallet you should create the [account configuration](account-configuration.md) first. Next use the following routine to attach the user account and switch the client object to the full state:

```typescript
async login(account: AccountConfig): Promise<void>
```

### Parameters

`account` - an account configuration with credentials and other parameters.

### Return value

No return value is required but you must wait until login is completed before the next library interaction.

{% hint style="info" %}
When login is finished the client will switch into the full mode state and all of the public routines are avialable fo use.
{% endhint %}

## <mark style="background-color:green;">Logout</mark>

To set the customer's wallet create the [account configuration](account-configuration.md) first. Next, use the following routine to attach the user account and switch the client object to the full state:

```typescript
async logout(): Promise<void>
```

### Return value

No return value is required but you must wait logout completed before the next library interaction.

{% hint style="info" %}
When logout is complete the client switches to the account-less state.
{% endhint %}

### Example

The client configuration `clientConfig` defined in [this example](../initializing-the-client/client-configuration.md#the-client-library-multipool-configuration-example)

```typescript
console.log('Attaching account...');
await client.login(accountConfig);
console.log('Seems all right!');

await client.logout();
console.log('See you later...');
```

## <mark style="background-color:green;">Is Account is Attached</mark>

Check library is in full mode:

```typescript
hasAccount(): boolean
```

### Return value

`true` if account is present and the library is working in full mode or `false` otherwise.

### Example

```typescript
const res = client.hasAccount()
console.log(`Library operates in ${res ? 'full' : 'account-less'} mode`);
```
