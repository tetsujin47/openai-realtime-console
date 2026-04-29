# OpenAI Realtime Console

[WebRTC](https://platform.openai.com/docs/guides/realtime-webrtc) を使って [OpenAI Realtime API](https://platform.openai.com/docs/guides/realtime) を利用する方法を示すサンプルアプリケーションです。

## インストールと使い方

はじめに OpenAI の API キーが必要です。[ダッシュボードで作成してください](https://platform.openai.com/settings/api-keys)。サンプルファイルから `.env` ファイルを作成し、API キーを設定します。

```bash
cp .env.example .env
```

ローカルで実行するには [Node.js](https://nodejs.org/) が必要です。依存パッケージをインストールします。

```bash
npm install
```

開発サーバーを起動します。

```bash
npm run dev
```

[http://localhost:3000](http://localhost:3000) でアプリケーションが起動します。

このアプリは [express](https://expressjs.com/) を使って [`/client`](./client) フォルダの React フロントエンドを提供する最小構成のテンプレートです。サーバーは [vite](https://vitejs.dev/) を使って React フロントエンドをビルドします。

WebRTC データチャネルを通じた Realtime API イベントの送受信方法と、クライアントサイドのファンクションコーリングの設定方法を示しています。UI のログパネルでクライアント・サーバーイベントの JSON ペイロードを確認することもできます。

## プロダクションビルド

プロダクション向けにビルドするには以下を実行します。

```bash
npm run build
```

React フロントエンドが `dist/client/` に、サーバーが `dist/server/` にコンパイルされます。ビルド後にプロダクションサーバーを起動するには以下を実行します。

```bash
npm run start
```

サーバーは `PORT` 環境変数（デフォルト: `3000`）を参照します。`OPENAI_API_KEY` の設定が必要です。

## インターネット上に公開する

Node.js に対応した任意のプラットフォームにホストできます。代表的なサービスの手順を以下に示します。

### Railway

1. コードを GitHub リポジトリにプッシュします。
2. [Railway](https://railway.app/) を開き、そのリポジトリから新しいプロジェクトを作成します。
3. Railway のプロジェクト設定で `OPENAI_API_KEY` 環境変数を追加します。
4. Railway が `npm run start` を自動検出してデプロイします。公開 URL はプロジェクトダッシュボードに表示されます。

### Render

1. コードを GitHub リポジトリにプッシュします。
2. [Render](https://render.com/) で新しい **Web Service** を作成し、リポジトリを連携します。
3. サービス設定で以下を入力します。
   - **Build Command**: `npm install && npm run build`
   - **Start Command**: `npm run start`
4. `OPENAI_API_KEY` を環境変数として追加します。
5. デプロイすると `*.onrender.com` の公開 URL が発行されます。

### Fly.io

1. [Fly CLI](https://fly.io/docs/hands-on/install-flyctl/) をインストールし、`fly auth login` でログインします。
2. プロジェクトディレクトリで以下を実行します。
   ```bash
   fly launch
   ```
3. API キーをシークレットとして設定します。
   ```bash
   fly secrets set OPENAI_API_KEY=<your-key-here>
   ```
4. デプロイします。
   ```bash
   fly deploy
   ```
5. `https://<app-name>.fly.dev` でアプリにアクセスできます。

より充実したサンプルとして、[OpenAI Swarm](https://github.com/openai/swarm) に着想を得たエージェントアーキテクチャを採用した Next.js 製の [OpenAI Realtime Agents](https://github.com/openai/openai-realtime-agents) デモもあります。

## 旧 WebSockets 版

クライアント側で WebSockets を使用していた旧バージョン（ブラウザでの使用は非推奨）は[こちら](https://github.com/openai/openai-realtime-console/tree/websockets)で確認できます。

## ライセンス

MIT
