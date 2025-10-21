# NiFi Mini Projects

Just playing around with Apache NiFi using Docker. This is a simple setup to learn how NiFi works.

## What's This?

A basic NiFi environment that runs locally. I built a simple flow that moves files from one folder to another. Nothing fancy, just learning the basics.

## What You Need

- Docker Desktop
- That's it

## How to Run

1. Clone this repo
2. Copy the env file:
   ```bash
   cp .env.example .env
   ```
3. Start everything:
   ```bash
   docker-compose up -d
   ```
4. Open NiFi at https://localhost:8443
   - Username: admin
   - Password: check your .env file

## The Flow I Built

Pretty simple:
- GetFile picks up files from `input-data` folder
- PutFile drops them in `output-data` folder

Saved it to NiFi Registry so I can track changes and reuse it later.

**Want to skip the setup?** Import the pre-built template from the `templates/` folder.

## How to Test

Drop any file in the `input-data` folder and it'll show up in `output-data`. 

```bash
echo "test" > input-data/test.txt
# check output-data folder
```

## Stopping It

```bash
docker-compose down
```

## NiFi Registry Setup

Connected NiFi to Registry for version control:
- Registry URL: http://nifi-registry:18080
- Bucket: "File Transfer Flow"
- Flow is now versioned and tracked

## Notes

- This is for learning, not production
- NiFi uses HTTPS (port 8443), Registry uses HTTP (port 18080) - fine for local testing
- Flow changes are tracked in NiFi Registry
- All the data persists in Docker volumes

---

Made this while learning NiFi. Feel free to use it if you're learning too.

