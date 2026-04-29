# OpenAI Realtime Console

This is an example application showing how to use the [OpenAI Realtime API](https://platform.openai.com/docs/guides/realtime) with [WebRTC](https://platform.openai.com/docs/guides/realtime-webrtc).

## Installation and usage

Before you begin, you'll need an OpenAI API key - [create one in the dashboard here](https://platform.openai.com/settings/api-keys). Create a `.env` file from the example file and set your API key in there:

```bash
cp .env.example .env
```

Running this application locally requires [Node.js](https://nodejs.org/) to be installed. Install dependencies for the application with:

```bash
npm install
```

Start the application server with:

```bash
npm run dev
```

This should start the console application on [http://localhost:3000](http://localhost:3000).

This application is a minimal template that uses [express](https://expressjs.com/) to serve the React frontend contained in the [`/client`](./client) folder. The server is configured to use [vite](https://vitejs.dev/) to build the React frontend.

This application shows how to send and receive Realtime API events over the WebRTC data channel and configure client-side function calling. You can also view the JSON payloads for client and server events using the logging panel in the UI.

## Building for production

To build the application for production, run:

```bash
npm run build
```

This compiles the React frontend into `dist/client/` and the server into `dist/server/`. To start the production server after building:

```bash
npm run start
```

The server reads the `PORT` environment variable (default: `3000`) and requires `OPENAI_API_KEY` to be set.

## Deploying to the internet

You can host this application on any platform that supports Node.js. Below are instructions for some common options.

### Railway

1. Push your code to a GitHub repository.
2. Open [Railway](https://railway.app/) and create a new project from that repository.
3. Add the `OPENAI_API_KEY` environment variable in the Railway project settings.
4. Railway automatically detects the `npm run start` start command and deploys the app. The public URL is shown in the project dashboard.

### Render

1. Push your code to a GitHub repository.
2. Create a new **Web Service** on [Render](https://render.com/) and connect the repository.
3. Set the following in the service settings:
   - **Build Command**: `npm install && npm run build`
   - **Start Command**: `npm run start`
4. Add `OPENAI_API_KEY` as an environment variable.
5. Deploy — Render provides a public `*.onrender.com` URL.

### Fly.io

1. Install the [Fly CLI](https://fly.io/docs/hands-on/install-flyctl/) and log in with `fly auth login`.
2. From the project directory, run:
   ```bash
   fly launch
   ```
3. Set your API key as a secret:
   ```bash
   fly secrets set OPENAI_API_KEY=<your-key-here>
   ```
4. Deploy with:
   ```bash
   fly deploy
   ```
5. Your app will be available at `https://<app-name>.fly.dev`.

For a more comprehensive example, see the [OpenAI Realtime Agents](https://github.com/openai/openai-realtime-agents) demo built with Next.js, using an agentic architecture inspired by [OpenAI Swarm](https://github.com/openai/swarm).

## Previous WebSockets version

The previous version of this application that used WebSockets on the client (not recommended in browsers) [can be found here](https://github.com/openai/openai-realtime-console/tree/websockets).

## License

MIT
