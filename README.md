# module-alias : React,React Native (include Expo),NextJS ,  NodeJS 
# Use Path Aliases with React  and VS Code : [jsconfig](https://code.visualstudio.com/docs/languages/jsconfig)
###  jsconfig.json
```
{
    "compilerOptions": {
      "module": "commonjs",
      "target": "es6",
      "baseUrl": "src",
     "paths": {
        "@components/*": ["components/*"],
        "@pages/*": ["pages/*"],
      }
    },
    "exclude": ["node_modules", ".vscode"]
  }
```
#  Use Path Aliases NodeJS  : [module-alias](https://www.npmjs.com/package/module-alias)
#  Use Path Aliases with NextJS and VS Code
###  jsconfig.json
```
{
    "compilerOptions": {
      "module": "commonjs",
      "target": "es6",
      "baseUrl": "src",
       "paths": {
        "@components/*": ["components/*"],
        "@pages/*": ["pages/*"],
      }
    
    },
    "exclude": ["node_modules", ".vscode"]
  }
```
#  Use Path Aliases with React Native and VS Code

Example : import SomeOtherComponent from '../../../SomeOtherPath/index.js 
=> import SomeOtherComponent from '@SomeOtherPath/index.js
| ALIAS NAME | ALIAS PATH*|
| ------ | ------ |
| @navigation |  ./src/navigation |  
| @components |  ./src/components |  
| @assets | ./assets |
## 1: Install library 
```
For npm:
npm i metro-react-native-babel-preset

For yarn:
yarn add -D metro-react-native-babel-preset
```
## 2 : Config

### 2.1  babel.config.js or  .babelrc 
```
module.exports = function (api) {
  api.cache(true);
  return {
    presets: ['babel-preset-expo'],
    plugins: ['inline-dotenv'],
    presets: ['module:metro-react-native-babel-preset'],
    plugins: [
      [
        'module-resolver',
        {
          root: ['.'],
          extensions: ['.ios.ts', '.android.ts', '.ts', '.ios.tsx', '.android.tsx', '.tsx', '.jsx', '.js', '.json'],
          alias: {
            '@assets': './assets',
            '@components': './components',
            '@helper': './helper',
            '@layouts': './layouts',
            '@pages': './pages',
            '@redux': './redux',
            '@utils': './utils',
            '@config': './config',
          },
        },
      ],
    ],
  };
};

```

### 2.2  jsconfig.json
```
{
    "compilerOptions": {
      "module": "commonjs",
      "target": "es6",
      "baseUrl": ".",
      "paths": {
        "@assets/*": ["./assets/*"],
        "@components/*": ["./components/*"],
        "@helper/*": ["./helper/*"],
        "@layouts/*": ["./layouts/*"],
        "@pages/*": ["./pages/*"],
        "@redux/*": ["./redux/*"],
        "@utils/*": ["./utils/*"],
        "@config/*": ["./config/*"],
      }
    },
    "exclude": ["node_modules", "web-build", ".expo", ".expo-shared", ".vscode"]
  }
```

> Reference :
> https://stackoverflow.com/questions/68675994/what-is-jsconfig-json
> https://mtateam.medium.com/how-to-use-import-aliases-with-react-native-and-vs-code-dadb246674c7
