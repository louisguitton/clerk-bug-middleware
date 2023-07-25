# clerk-bug-middleware

> Minimal reproducible example for the issue discussed [here](https://github.com/clerkinc/clerk-next-app-router-starter/issues/2)

## Usage

First setup your clerk app and replace the env variables from .env.example in your .env.local

```sh
npm i
npm run dev
```

Then:

- `open http://localhost:3000/` -> this works, as expected
- `open http://localhost:3000/expected-unmatched` -> this does not work, as expected
- `open http://localhost:3000/error` -> this does not work and this is the issue

## Notes

In my findings, static pages seem to be the culprit.
For example, the line

```ts
export const dynamic = "force-static";
```

for the /error page triggers the error.
But if you add back `"use client"` to the page, the error disappears.
