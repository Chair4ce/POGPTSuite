# The POGPT Suite

The Portable Operational gPT Suite, an open-source AI chat app designed for all computing environments.

Prototyped and developed at the [DAF BRAVO 11 Hackathon](https://www.defense.gov/News/Releases/Release/Article/3610215/chief-digital-and-artificial-intelligence-office-to-host-hackathon-in-hawaii/) from February 05 to 09, 2024 by team Mai Tai Mafia.

<img src="./public/readme/screenshot.png" alt="Chatbot UI" width="600">

## Demo Site

View the latest demo [here](https://pogpt.ambercaravalho.com).

## Updating (Once Installed)

In your terminal at the root of your local POGPT Suite repository, run:

```bash
npm run update
```

## Initial Build Guide (Linux Only)

Follow these steps to get your own POGPT Suite instance running locally.

### 1. Clone this GitHub Repo

```bash
git clone https://github.com/Chair4ce/POGPTSuite.git
```

### 2. Install Dependencies

Open a terminal in the root directory of your local POGPT Suite repository and run:

```bash
npm install
```

### 3. Install Supabase

#### 1. Install Docker

You will need to install Docker to run Supabase locally. You can download it [here](https://docs.docker.com/get-docker) for free.

#### 2. Add your user account to the local docker user group.

```bash
sudo usermod -aG docker $USER
```

You may need to log out and back into your account for the permissions to apply.

#### 3. Install Supabase CLI

Homebrew is required to install Supabase. If it is not installed already, run:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Once Homebrew is installed, run:

```bash
brew install supabase/tap/supabase
```

#### 4. Start Supabase

In your terminal at the root of your local POGPT Suite repository, run:

```bash
supabase start
```

### 5. Fill in Secrets

#### 1. Environment Variables

In your terminal at the root of your local POGPT Suite repository, run:

```bash
cp .env.local.example .env.local
```

Get the required values by running:

```bash
supabase status
```

Note: Use `API URL` from `supabase status` for `NEXT_PUBLIC_SUPABASE_URL`.

Now go to your `.env.local` file and fill in the values.

If the environment variable is set, it will disable the input in the user settings.

#### 2. SQL Setup

In the 1st migration file, `supabase/migrations/20240108234540_setup.sql`, you will need to replace 2 values with the values you got above:

- `project_url` (line 53): `http://supabase_kong_chatbotui:8000` (default) can remain unchanged if you don't change your `project_id` in the `config.toml` file
- `service_role_key` (line 54): You got this value from running `supabase status`

### 6. Install Ollama

Follow the instructions [here](https://github.com/jmorganca/ollama).

### 7. Run app locally

In your terminal at the root of your local POGPT Suite repository, run:

```bash
npm run chat
```

Your local instance of POGPT Suite should now be running at [http://localhost:3000](http://localhost:3000). Be sure to use a compatible node version (i.e. v18).

You can view your backend GUI at [http://localhost:54323/project/default/editor](http://localhost:54323/project/default/editor).

## Discussions

We highly encourage you to participate in the "Discussions" tab above!

Discussions are a great place to ask questions, share ideas, and get help.

Odds are if you have a question, someone else has the same question.
