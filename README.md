# WAFRN SDK

[Wafrn](https://app.wafrn.net/) SDK for Node.js

## Installation

```bash
npm i dotenv
npm i wafrn-sdk
```

## Usage

```ts
import "dotenv/config";
import { login, sendWoot } from "wafrn-sdk";

async function main() {
  const token = await login();
  await sendWoot("Hello World", { token });
}
```

## Available methods

### login

Takes your username `WAFRN_EMAIL` and password `WAFRN_PASSWORD` from the environment and returns a token to be used in other methods.

#### Syntax

```ts
const token = await login();
```

#### Parameters

None

#### Return value

If username and password are correct, a Promise that resolves to the authorization token from Wafrn.

### sendWoot

Send a woot.

#### Syntax

```ts
await sendWoot(text, options);
```

#### Parameters

`text` Text

`options` Object containing:

- `token`: string. Required.
- `privacy`: number. Optional. Defaults to `0` being public.
- `parent`: string. Optional. Woot id that this woot is a reply of.

### sendPrivateWoot

Send a woot that is private.

#### Syntax

```ts
await sendPrivateWoot(text, options);
```

### Parameters

`text` Text

`options` Object containing:

- `token`: string. Required.

#### Return value

An empty Promise.

### sendPrivateReplyWoot

Send a private woot that is a reply.

#### Syntax

```ts
await sendPrivateReplyWoot(text, options);
```

#### Parameters

`text` Text

`options` Object containing:

- `token`: string. Required.

#### Return value

An empty Promise.

### getDms

#### Syntax

```ts
const {
  data: { users, posts },
} = await getDms(options);
```

#### Parameters

`options` Object containing:

- `token`: string. Required.

#### Return value

It returns a Promise that resolves to the latest dms and their users.

`data` Object containing:

- `users`: Array of objects of type:
  - `avatar`: string
  - `banned`: boolean
  - `bskyDid`: string
  - `id`: string
  - `isBlueskyUser`: boolean
  - `isFediverseUser`: boolean
  - `name`: string
  - `remoteId`: any
  - `url`: string
- `posts`: Array of objects of type:
  - `ancestors`: array of ancestor posts
  - `bskyCid`: any
  - `bskyUri`: any
  - `content`: string
  - `content_warning`: string
  - `createdAt`: string
  - `featured`: boolean
  - `hierarchyLevel`: number
  - `id`: string
  - `isDeleted`: boolean
  - `isReblog`: boolean
  - `markdownContent`: string
  - `notes`: number
  - `parentId`: string
  - `privacy`: number
  - `remotePostId`: any
  - `title`: any
  - `updatedAt`: string
  - `userId`: string
