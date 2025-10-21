# NiFi Flow Templates

## Available Templates

### File_Transfer_Flow.json
Simple file transfer flow with GetFile and PutFile processors.

**What it does:**
- Monitors `/opt/input-data` for new files
- Automatically moves them to `/opt/output-data`
- Auto-terminates successful transfers
- Retries on failure

## How to Import

1. In NiFi, click the **Import** button (upload icon) in the toolbar
2. Select `File_Transfer_Flow.json`
3. The "File Transfer Flow" process group will appear on your canvas
4. Double-click it to see the processors inside
5. Right-click on the canvas inside and select "Start" to run the flow

## What's Inside

- **GetFile**: Picks up files from `/opt/input-data`
- **PutFile**: Writes files to `/opt/output-data`
- **Connection**: GetFile → PutFile on success
- **Retry Loop**: PutFile → PutFile on failure

## Customizing

Right-click any processor and select "Configure" to modify:
- Input/output directories
- File filtering patterns (currently accepts all non-hidden files)
- Scheduling intervals
- Batch sizes
