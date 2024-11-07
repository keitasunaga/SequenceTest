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
npx create-expo-app SequenceTest --template expo-template-blank@51.0.0
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
