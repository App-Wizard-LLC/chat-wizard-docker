# Mattermost Docker
The official Docker deployment solution for Mattermost.

## Install & Usage

### Step 1: Prepare Environment
1. **Create the `.env` file**  
   Run the following command to create the `.env` file:  
   ```bash
   make .env
   ```
2. **Copy environment variables**  
   Copy `env.example` to `.env`.  

3. **Update domain**  
   Update the `DOMAIN` variable at the top of the `.env` file to `localhost` or any domain you want to deploy on.

### Step 2: Set Up Directories
Run the following commands individually to create the required directory structure:  
```bash
mkdir volumes/app/mattermost/config
mkdir volumes/app/mattermost/data
mkdir volumes/app/mattermost/logs
mkdir volumes/app/mattermost/plugins
mkdir volumes/app/mattermost/client/plugins
mkdir volumes/app/mattermost/bleve-indexes
```

### Step 3: Set Permissions
1. **Windows (Command Prompt)**  
   Run Command Prompt as administrator and navigate to the directory. Then, execute:  
   ```cmd
   icacls .\volumes\app\mattermost\ /grant "Everyone":(F) /T
   ```
   This is equivalent to the Linux `chown` command.

2. **Linux**  
   If using Linux, set the necessary permissions:  
   ```bash
   sudo chown -R 2000:2000 ./volumes/app/mattermost
   ```

### Step 4: Start the Application
Run the following Docker Compose command to start Mattermost:  
```bash
docker compose -f docker-compose.yml -f docker-compose.without-nginx.yml up -d
```

## Contribute
PRs are welcome, refer to our [contributing guide](https://developers.mattermost.com/contribute/getting-started/) for an overview of the Mattermost contribution process.

## Upgrading from `mattermost-docker`

This repository replaces the [deprecated mattermost-docker repository](https://github.com/mattermost/mattermost-docker). For an in-depth guide to upgrading, please refer to [this document](https://github.com/mattermost/docker/blob/main/scripts/UPGRADE.md).
