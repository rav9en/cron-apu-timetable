# Cron APU Timetable

Automatic CRON job for fetching APU timetable and updating in personal Google Calendar.

### Prerequisites
1. [node.js](https://nodejs.org/en/download)
2. [git](https://git-scm.com/downloads)
3. a [cloudflare](https://www.cloudflare.com/) account
4. a [gcp](https://cloud.google.com/) account

## Getting Started

First, clone the repository and install the dependencies.

```
git clone https://github.com/Hackthletes-APU/cron-apu-timetable.git

cd cron-apu-timetable

npm install
```

Next, let's setup and configure all the `enviroment variables` needed to run the project.

Create a new file called `.env` and copy the contents from `.env.example` and paste it into the newly created file.

It should look something like this:
```

// .env
APU_TIMETABLE_S3="S3 PUBLIC LINK"
INTAKE_CODE="YOUR INTAKE CODE"

## GOOGLE SERVICE ACCOUNT VARIABLES
CALENDAR_ID="YOUR CALENDAR ID" // Target Calendar ID
PROJECT_ID="YOUR PROJECT ID" // Obtianed from your service account JSON file
PRIVATE_KEY_ID="YOUR PRIVATE KEY ID" Obtianed from your service account JSON file
PRIVATE_KEY="YOUR PRIVATE KEY" Obtianed from your service account JSON file
CLIENT_EMAIL="YOUR CLIENT EMAIL" Obtianed from your service account JSON file
CLIENT_ID="YOUR CLIENT ID" Obtianed from your service account JSON file
CLIENT_CERT_URL="YOUR CLIENT CERT URL" Obtianed from your service account JSON file

```

To obtain the `GOOGLE SERVICE ACCOUNT VARIABLES` you will need to create a new service account in your GCP console and download the JSON file.

All the following variables will be inside.

Once you have all the variables setup, you need to configure `fetchTimetable.js`

```
// fetchTimetable.js

# Modify the array to your electives (leave empty if none).

const nonElectives = [];
```

Once you have done all the above steps, you can now test run the job using the command.

```
node index.js
```

## Deploying on Cloudflare Workers

Create a new file called `wrangler.toml` and copy the contents from `wrangler-sample.toml` and paste it into the newly created file.

After setting up the `wrangler.toml` file, you can now deploy the project to Cloudflare Workers using the steps followed.

```
wrangler login
wrangler deploy
```

Read more about wrangler configuration [here](https://developers.cloudflare.com/workers/wrangler/).
