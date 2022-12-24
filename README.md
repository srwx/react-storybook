# React with tailwindcss + Storybook

<div align="center">
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="react" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="tailwindcss" />
  <img src="https://img.shields.io/badge/storybook-FF4785?style=for-the-badge&logo=storybook&logoColor=white" alt="storybook" />
</div>

## Versioning
- tailwindcss: v3<br />
- postcss: v8<br />
- @storybook/react: v6<br />

## Step
1.) Setup tailwindcss to project. (For React project, follow [tailwind guide](https://tailwindcss.com/docs/installation).)<br /><br />

2.) Init storybook with npx command:
```
npx sb init
```
<br />

3.) Install these dependencies:
```
yarn add -D @storybook/builder-webpack5 @storybook/manager-webpack5 postcss-loader webpack
```
<br />

4.) Add these config in `.storybook/main.js`
```js
const path = require("path");

module.exports = {
  // ...
  
  webpackFinal: (config) => {
    config.module.rules.push({
      test: /\.css$/,
      use: [
        {
          loader: "postcss-loader",
          options: {
            postcssOptions: {
              plugins: [require("tailwindcss"), require("autoprefixer")],
            },
          },
        },
      ],
      include: path.resolve(__dirname, "../"),
    });
    return config;
  },
};
```
<br />

5.) Import global.css file to `.storybook/preview.js`
```js
import "../src/global.css";
```

