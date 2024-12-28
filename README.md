## Step 1: Add the PHP repository and update package list
```bash
sudo add-apt-repository ppa:ondrej/php
sudo apt update
```

## Step 2: Install PHP versions and required extensions
### Install PHP 8.0
```bash
sudo apt install php8.0-cli php8.0-curl php8.0-mbstring php8.0-xml php8.0-mysql
```

### Install PHP 8.1
```bash
sudo apt install php8.1-cli php8.1-curl php8.1-mbstring php8.1-xml php8.1-mysql
```

### Install PHP 8.2
```bash
sudo apt install php8.2-cli php8.2-curl php8.2-mbstring php8.2-xml php8.2-mysql
```

### Install PHP 8.3
```bash
sudo apt install php8.3 php8.3-cli php8.3-common php8.3-mbstring php8.3-xml php8.3-curl php8.3-zip php8.3-mysql
```

## Step 3: Set the default PHP version (example: set PHP 8.2 as default)
```bash
sudo update-alternatives --set php /usr/bin/php8.2
sudo update-alternatives --set phpize /usr/bin/phpize8.2
sudo update-alternatives --set php-config /usr/bin/php-config8.2
```

## Step 4: Switch between PHP versions
### Switch the PHP version
```bash
sudo update-alternatives --config php
```

### Switch the `phpize` version
```bash
sudo update-alternatives --config phpize
```

### Switch the `php-config` version
```bash
sudo update-alternatives --config php-config
```

## Step 5: Display the current PHP version and configuration
```bash
sudo update-alternatives --display php
```

## Step 6: Change the PHP version again (if needed)
```bash
sudo update-alternatives --config php
```

## Step 7: Install PostgreSQL and PostgreSQL Client
### Update and install PostgreSQL and its client
```bash
sudo apt-get update
sudo apt-get install postgresql postgresql-contrib
sudo apt-get install postgresql-client
```

### Check the installed version of PostgreSQL
```bash
psql --version
```

## Step 8: Start and check the status of PostgreSQL service
```bash
sudo service postgresql start
sudo systemctl status postgresql
```

### Check PostgreSQL processes
```bash
ps aux | grep postgres
```

## Step 9: Configure PostgreSQL and create a database
### Log in as the 'postgres' user
```bash
sudo -u postgres psql
```

### Change the password for the postgres user
```bash
ALTER USER postgres WITH PASSWORD 'password';
```

### Create a new database
```bash
CREATE DATABASE system_pos;
```

### Exit PostgreSQL
```bash
\q
```

## Step 10: Configure Laravel to use PostgreSQL
### Update the `.env` file for Laravel database configuration
```ini
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=system_pos
DB_USERNAME=postgres
DB_PASSWORD=password
```

### Clear the Laravel configuration cache
```bash
php artisan config:clear
```

### Run Laravel migrations
```bash
php artisan migrate
```

## Step 11: Verify the PostgreSQL database setup
### Log in to PostgreSQL and check the tables in the database
```bash
psql -h 127.0.0.1 -U postgres -d system_pos
\dt
```

## Step 12: Additional PostgreSQL commands
### View the PostgreSQL log for troubleshooting
```bash
sudo tail -f /var/log/postgresql/postgresql-12-main.log
```

### Restart the PostgreSQL service
```bash
sudo service postgresql restart
```
