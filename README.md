[![ci-build-status](https://img.shields.io/github/actions/workflow/status/greencoast-studios/djs-extended-data-provider-level/push.yml?logo=github&label=build)](https://github.com/greencoast-studios/djs-extended-data-provider-level)
[![issues](https://img.shields.io/github/issues/greencoast-studios/djs-extended-data-provider-level?logo=github)](https://github.com/greencoast-studios/djs-extended-data-provider-level)
[![bundle-size](https://img.shields.io/bundlephobia/min/@greencoast/djs-extended-data-provider-level)](https://www.npmjs.com/package/@greencoast/djs-extended-data-provider-level)
[![node-version](https://img.shields.io/node/v/@greencoast/djs-extended-data-provider-level?logo=Node.js&color=green)](https://www.npmjs.com/package/@greencoast/djs-extended-data-provider-level)
[![version](https://img.shields.io/npm/v/@greencoast/djs-extended-data-provider-level?logo=npm)](https://www.npmjs.com/package/@greencoast/djs-extended-data-provider-level)
[![djs-extended-version](https://img.shields.io/npm/dependency-version/@greencoast/djs-extended-data-provider-level/peer/@greencoast/discord.js-extended?logo=npm)](https://www.npmjs.com/package/@greencoast/djs-extended-data-provider-level)
[![downloads-week](https://img.shields.io/npm/dw/@greencoast/djs-extended-data-provider-level?logo=npm)](https://www.npmjs.com/package/@greencoast/djs-extended-data-provider-level)
[![downloads-total](https://img.shields.io/npm/dt/@greencoast/djs-extended-data-provider-level?logo=npm)](https://www.npmjs.com/package/@greencoast/djs-extended-data-provider-level)

# Discord.js - Extended / Level Data Provider

[djs-extended-data-provider-level](https://github.com/greencoast-studios/djs-extended-data-provider-level) is an implementation of a
[DataProvider](https://docs.greencoaststudios.com/discord.js-extended/master/classes/Discord_js_Extended.DataProvider.html) for
[discord.js-extended](https://docs.greencoaststudios.com/discord.js-extended/master/index.html) made with a [LevelDB](https://www.npmjs.com/package/level) backend.

## Usage

You can visit the [documentation site](https://docs.greencoaststudios.com/djs-extended-data-provider-level/master) to see what this utility offers.

### Installation

This package is designed to work for [discord.js](https://www.npmjs.com/package/discord.js) and [@greencoast/discord.js-extended](https://www.npmjs.com/package/@greencoast/discord.js-extended),
this does not install any of these packages, you are expected to have these in your project.

You can install this package with:

```text
npm install discord.js @greencoast/discord.js-extended @greencoast/djs-extended-data-provider-level
```

## Adding the Data Provider to your Client

Assuming you have created your own [ExtendedClient](https://docs.greencoaststudios.com/discord.js-extended/master/classes/Discord_js_Extended.ExtendedClient.html),
you can attach this data provider into your client as such:

```js
const { LevelDataProvider } = require('@greencoast/djs-extended-data-provider-level');

const client = new ExtendedClient();

client.once('ready', async () => {
  await client.setDataProvider(new LevelDataProvider(client, 'database_location'));
});
```

And that's it! You can then access the data provider across your code through `client.dataProvider`.

### Using Data Provider

You can use the following methods anywhere:

```js
await client.dataProvider.get(guild, 'key'); // Get a value for 'key' in guild.
await client.dataProvider.set(guild, 'key', 'value'); // Set 'value' for 'key' in guild.
await client.dataProvider.delete(guild, 'key'); // Delete a key-value pair for 'key' in guild.
await client.dataProvider.clear(guild); // Clear all data in a guild.

await client.dataProvider.getGlobal('key'); // Get a value for 'key' in the global scope.
await client.dataProvider.setGlobal('key', 'value'); // Set 'value' for 'key' in the global scope.
await client.dataProvider.deleteGlobal('key'); // Delete a key-value pair for 'key' in the global scope.
await client.dataProvider.clearGlobal(); // Clear all data in the global scope.
```

If you're using TypeScript, you should pass a generic type to the `get` and `delete` methods as such:

```ts
await client.dataProvider.get<string>(guild, 'key'); // Promise<string | undefined>
await client.dataProvider.get<string>(guild, 'key', 'default'); // Promise<string>

await client.dataProvider.delete<string>(guild, 'key'); // Promise<string | undefined>
```

## Testing

You can run the unit tests for this package by:

1. Cloning the repo:

```text
git clone https://github.com/greencoast-studios/djs-extended-data-provider-level
```

2. Installing the dependencies.

```text
npm install
```

3. Running the tests.

```text
npm test
```

## Authors

This utility library was made by [Greencoast Studios](https://greencoaststudios.com).
