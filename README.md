# ezuikit_rec_demo

## Use

```bash

# npm
npm install

# yarn
yarn install

# pnpm
pnpm install

# development
npm run serve

# build production
npm run build

```

## staticPath

```ts
player = new RecTheme({
  id: "video-container", // container id
  accessToken,
  url,
  width: 600,
  height: 400,
  staticPath: "/", // Currently, no CDN is provided. Locally specify the path of a static resource
  autoPlay: true,
  env: { domain },
});
```

`staticPath` is the path of a dependent static resource, and sdk does not provide a CDN.

Copy `node_modules/@ezuikit/theme-rec/dist/PlayCtrlWasm` to `public/PlayCtrlWasm`
