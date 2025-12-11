# React + TypeScript + Vite

英語版: [README.md](README.md)

このテンプレートは、ViteでReactをHMRといくつかのESLintルールとともに動作させるための最小セットアップを提供します。

日本語版: このファイル (README_ja.md)

## Reactコンパイラ

このテンプレートでは、開発とビルドのパフォーマンスへの影響のためReact Compilerは有効になっていません。有効化するには次のドキュメントを参照してください: https://react.dev/learn/react-compiler/installation

## ESLint設定の拡張

本番アプリケーションを開発している場合は、型認識のあるルールを有効にするよう設定を更新することをお勧めします。

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

英語版: [README.md](README.md)
