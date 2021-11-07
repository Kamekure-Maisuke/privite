# vue3 and vite and tailwind

## 手順

```bash
npm init vite@latest front -- --template vue
cd front
npm i
npm install vue-router@4
```

- 任意でtailwindcssを入れる。

```bash
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest

npx tailwindcss init -p
```

- assetsディレクトリを作り、その中に`tailwind.css`を作り、中身を以下にする。

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

- その後、`src/main.js`に以下の加える。

```js
import './assets/css/tailwind.css'
```

- 任意でdaisyuiを入れる。

```bash
npm i daisyui
```

```js
plugins: [
  require('daisyui'),
],
daisyui: {
  themes: false
}
```