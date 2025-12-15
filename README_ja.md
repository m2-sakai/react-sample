# React + TypeScript + Vite

このテンプレートは、ViteでReactをHMRといくつかのESLintルールと共に動作させるための最小限のセットアップを提供します。

English README: [README.md](README.md)

現在、2つの公式プラグインが利用可能です:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) はFast Refreshに[Babel](https://babeljs.io/)（または[rolldown-vite](https://vite.dev/guide/rolldown)で使用される場合は[oxc](https://oxc.rs)）を使用します
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) はFast Refreshに[SWC](https://swc.rs/)を使用します

## React Compiler

このテンプレートでは、開発とビルドのパフォーマンスに与える影響のため、React Compilerは有効になっていません。有効にするには、こちらのドキュメントを参照してください: https://react.dev/learn/react-compiler/installation

## ESLint構成の拡張

プロダクションアプリケーションを開発する場合は、型認識のあるlintルールを有効にするために設定を更新することをお勧めします。例:

```js
export default defineConfig([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...

      // Remove tseslint.configs.recommended and replace with this
      tseslint.configs.recommendedTypeChecked,
      // Alternatively, use this for stricter rules
      tseslint.configs.strictTypeChecked,
      // Optionally, add this for stylistic rules
      tseslint.configs.stylisticTypeChecked,

      // Other configs...
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```

他にもReact固有のlintルールのために[eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x)や[eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom)をインストールして利用できます。

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x'
import reactDom from 'eslint-plugin-react-dom'

export default defineConfig([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...
      // Enable lint rules for React
      reactX.configs['recommended-typescript'],
      // Enable lint rules for React DOM
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```
