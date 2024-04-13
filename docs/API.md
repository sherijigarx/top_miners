
# Audio Innovation API - Version 1.0

Welcome to the realm of audio innovation! Our suite of services transforms text into captivating spoken narratives, melodious tunes, and unique vocal identities, enhancing your audio experiences.

## Services

1. **Text-to-Speech (TTS)**: Converts text into spoken audio, ideal for narrations, announcements, or interactive voice responses.

2. **Text-to-Music (TTM)**: Transforms text into musical compositions, perfect for background music, jingles, or soundtracks.

3. **Voice Clone (VC)**: Generates customized voice clones from provided audio inputs and text, suitable for personalized voice applications.

## Setting Up and Configuring the Database

Follow these steps to create and configure the PostgreSQL database necessary for using the TTS, TTM, and VC services.

### Step 1: Install PostgreSQL

```bash
sudo apt-get update
sudo apt-get install postgresql postgresql-client postgresql-client-common
```

### Step 2: Check PostgreSQL Service Status

```bash
sudo service postgresql status
# If not running, start the service
sudo service postgresql start
```

### Step 3: Access PostgreSQL CLI as Superuser

```bash
sudo -u postgres psql
```

### Step 4: Create a New Role

```sql
CREATE ROLE user_role WITH LOGIN PASSWORD 'your_password' CREATEDB;
# To drop this role if necessary
DROP ROLE user_role;
```

### Step 5: Grant Necessary Privileges

```sql
ALTER ROLE user_role CREATEDB;
```

### Step 6: Verify the New Role

```sql
\du
```

### Step 7: Connect to PostgreSQL Database

```bash
createdb -h localhost -U user_role your_database
psql -h localhost -U user_role your_database
# or
psql -h localhost -U user_role -d your_database
```

### Removing Database

```sql
DROP DATABASE database_name_to_drop;
```

## Adding Secret Keys and Environment Variables

### Step 1: Open .bashrc File

```bash
cd ~
nano .bashrc
```

### Step 2: Add Secret Keys

Add the following lines to the `.bashrc` file:

```bash
export LOGIN_SECRET_KEY='your_secret_key_here'
export ADMIN_SECRET_KEY='your_secret_key_here'
export SECRET_KEY='your_secret_key_here'
export DATABASE_URL='postgresql://user_role:your_database_password@host:port/database_name'
```

### Step 3: Apply Changes

```bash
source .bashrc
```

### Step 4: Verify Environment Variables

```bash
echo $SECRET_KEY
echo $DATABASE_URL
```

## Adding Auth_Secret_Key to Database

```bash
cd ~/AudioSubnet/app
python key_add.py
# or
python3 key_add.py
```

## Creating Admin with All Privileges

```bash
python admin_database.py
# or
python3 admin_database.py
```

## Password Policy Requirement

Ensure that your passwords meet the following criteria:
- Length: 8-16 characters
- At least one uppercase letter
- At least one lowercase letter
- At least one digit
- At least one special character


## Youtube video as a reference

For API usage and top miner query, Please watch the [video](https://www.youtube.com/watch?v=UaMXiyDkPbQ&ab_channel=BittAudio-BittensorSN16)