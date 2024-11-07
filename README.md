# SequenceTest


このプロジェクトは、Expo SDK 51.0.0とReact Native 0.74.3を使用して作成されたReact Nativeアプリケーションです。セットアップから実行、GitHubへのpushまでの手順は以下の通りです。

---

## はじめに

### 前提条件
- [Node.js](https://nodejs.org/)をインストールしてください（未インストールの場合）。node18 or 20推奨
- Expo CLIをグローバルにインストールするのも便利です（任意）:
  ```bash
  npm install -g expo-cli
  ```

### 1. Expoプロジェクトの作成
Expoプロジェクトを作成し、特定のExpo SDKおよびReact Nativeのバージョンを指定するために、以下のコマンドを使用します。

```bash
npx create-expo-app SequenceTest
npm install react-native-web@~0.19.10 react-dom@18.2.0 @expo/metro-runtime@~3.2.3
```

- `npx create-expo-app`は、Expoプロジェクトをセットアップするためのコマンドです。
- `SequenceTest`はプロジェクト名で、任意の名前に変更できます。
- `expo-template-blank@51.0.0`は、Expo SDK 51.0.0を指定するためのテンプレートです。これにより、対応するReact Nativeバージョン（この場合は0.74.3）も自動的に設定されます。
- `react-native-web@~0.19.10`は、WEBで開発するために入れています。必要がない場合は入れなくてOK

このコマンドを実行すると、指定のバージョンでExpoプロジェクトが作成されます。

### 2. アプリケーションの実行
プロジェクトをローカルで実行し、実機またはシミュレータでテストする手順は以下の通りです。

1. **プロジェクトディレクトリに移動**
   ```bash
   cd SequenceTest
   ```

2. **Expo開発サーバーを起動**
   ```bash
   npx expo start
   ```

   - `npx expo start`を実行すると、Expoの開発サーバーが起動し、QRコードが表示されます。

3. **端末またはシミュレータでアプリを開く**
   - **実機でテストする場合**: iOSまたはAndroidの端末にExpo Goアプリをインストールします。QRコードをExpo Goアプリでスキャンし、アプリを開きます。
     - [Expo Go for iOS](https://apps.apple.com/app/expo-go/id982107779)
     - [Expo Go for Android](https://play.google.com/store/apps/details?id=host.exp.exponent)
   - **シミュレータでテストする場合**: ターミナルで`i`または`a`を入力して、iOSまたはAndroidのシミュレータでアプリを起動します。シミュレータのセットアップが完了していない場合は、追加の設定が必要です。

3. **Error Tips**
   - **Error: EMFILE: too many open files**: 監視しているファイルが多すぎるので、watchmanを入れるか、watchmanが監視しているファイルをリセットすること
   ```bash
   brew install watchman
   ```

   ```bash
   watchman watch-del-all 
   ```
4. 利用ライブラリ
   | ライブラリ名                             | 開発者             | 役割                                                                                     |
   |------------------------------------------|--------------------|------------------------------------------------------------------------------------------|
   | `@0xsequence/waas`                       | 0xSequence         | Sequence Wallet as a Service (WaaS) SDKで、ウォレットの作成、管理、トランザクションの送信など、ブロックチェーンウォレットの機能を提供します。 |
   | `@0xsequence/react-native`               | 0xSequence         | React Native向けのSequence SDKで、モバイルアプリケーションでのウォレット機能の統合を容易にします。 |
   | `ethers@5.7.2`                           | Richard Moore      | Ethereumと対話するための軽量なJavaScriptライブラリで、スマートコントラクトのデプロイやトランザクションの送信などをサポートします。 |
   | `react-native-quick-crypto`              | Margelo            | React Native環境でNode.jsの`crypto`モジュールを高速に実装したライブラリで、暗号化機能を提供します。 |
   | `react-native-mmkv`                      | Marc Rousavy       | 高速なキー・バリュー型のストレージを提供するライブラリで、React Nativeアプリでのデータ保存に使用されます。 |
   | `react-native-keychain`                  | Joel Arvidsson     | iOSのKeychainとAndroidのKeystoreにアクセスし、パスワードやトークンなどの機密情報を安全に保存・取得するためのライブラリです。 |
   | `babel-plugin-module-resolver`           | Twin               | Babelのプラグインで、モジュールのインポートパスをエイリアス化し、コードの可読性と保守性を向上させます。 |
   | `expo-web-browser`                       | Expo               | システムのWebブラウザを使用してURLを開くためのAPIを提供し、リダイレクトの処理もサポートします。 |
   | `expo-auth-session`                      | Expo               | Webブラウザベースの認証（例：OAuthフロー）をアプリに統合するためのライブラリで、`expo-web-browser`上に構築されています。 |
   | `@invertase/react-native-apple-authentication` | Invertase     | iOSおよびAndroidでのApple認証（Sign in with Apple）をサポートするReact Nativeライブラリです。 |
   | `react-native-url-polyfill`              | Charles Mangwa     | React Native環境でのURLとURLSearchParamsのポリフィルを提供し、標準的なURL操作を可能にします。 |
   | `web-streams-polyfill`                   | Mattias Buelens    | WHATWG Streams標準のポリフィルで、ストリームAPIをサポートしていない環境での使用を可能にします。 |


   ```bash
   npm install @0xsequence/waas ethers@latest
   npm install @0xsequence/react-native react-native-quick-crypto react-native-mmkv react-native-keychain babel-plugin-module-resolver
   npm install expo-web-browser expo-auth-session @invertase/react-native-apple-authentication
   npm install react-native-url-polyfill web-streams-polyfill     
   ```