# NiFi Mini Projects

Built this to understand NiFi data flows and containerized pipeline architecture. Uses Docker, NiFi Registry for version control, and implements basic file transfer patterns as a foundation.

## What's This?

A local NiFi environment to explore flow concepts like processors, connections, and backpressure handling. Started with a simple file ingestion pattern to understand how data moves through NiFi pipelines.

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

## What I Learned

Through this project, I explored:
- NiFi flow architecture (processors, connections, relationships)
- Docker Compose for managing multi-container environments
- NiFi Registry integration for flow version control
- Volume mounts and data persistence patterns
- Basic security setup (environment variables, HTTPS vs HTTP considerations)

## NiFi Registry Setup

Connected NiFi to Registry for flow versioning:
- Registry URL: http://nifi-registry:18080
- Bucket: "File Transfer Flow"
- Flow changes are tracked and can be rolled back

## Troubleshooting Notes

Issues I ran into:
- **NiFi Registry permissions**: Had to run as root user for database access
- **Volume mounts**: Files created locally appear instantly in containers
- **Port conflicts**: NiFi defaults to 8443 (HTTPS), Registry on 18080 (HTTP)
- **Startup time**: NiFi takes 2-3 minutes to fully initialize

## Next Steps

Planning to add:
- S3 integration for cloud storage patterns
- Multi-flow scenarios (split, merge, route)
- Basic monitoring setup to understand NiFi metrics
- Error handling and retry patterns

## Notes

- Local development setup, not production-ready
- Credentials managed via .env file (not committed)
- All data persists in Docker volumes
- Flow template available in `templates/` for quick import

