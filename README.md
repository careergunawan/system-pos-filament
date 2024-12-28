# Step 1: Add the PHP repository and update package list
sudo add-apt-repository ppa:ondrej/php
sudo apt update

# Step 2: Install PHP versions and required extensions
# Install PHP 8.0
sudo apt install php8.0-cli php8.0-curl php8.0-mbstring php8.0-xml php8.0-mysql

# Install PHP 8.1
sudo apt install php8.1-cli php8.1-curl php8.1-mbstring php8.1-xml php8.1-mysql

# Install PHP 8.2
sudo apt install php8.2-cli php8.2-curl php8.2-mbstring php8.2-xml php8.2-mysql

# Install PHP 8.3
sudo apt install php8.3 php8.3-cli php8.3-common php8.3-mbstring php8.3-xml php8.3-curl php8.3-zip php8.3-mysql

# Step 3: Set the default PHP version (example: set PHP 8.2 as default)
sudo update-alternatives --set php /usr/bin/php8.2
sudo update-alternatives --set phpize /usr/bin/phpize8.2
sudo update-alternatives --set php-config /usr/bin/php-config8.2

# Step 4: Switch between PHP versions
# To switch the PHP version, use the following commands:
# This will prompt you to choose the PHP version to set as default
sudo update-alternatives --config php

# To switch the phpize version
sudo update-alternatives --config phpize

# To switch the php-config version
sudo update-alternatives --config php-config

# Step 5: Display the current PHP version and configuration
# This will show the current configured PHP version
sudo update-alternatives --display php

# Step 6: Change the PHP version again (if needed)
# To change the PHP version again, run the command:
sudo update-alternatives --config php

# Step 7: Install PostgreSQL and PostgreSQL Client
# Update and install PostgreSQL and its client
sudo apt-get update
sudo apt-get install postgresql postgresql-contrib
sudo apt-get install postgresql-client

# Check the installed version of PostgreSQL
psql --version

# Step 8: Start and check the status of PostgreSQL service
sudo service postgresql start
sudo systemctl status postgresql

# Check PostgreSQL processes
ps aux | grep postgres

# Step 9: Configure PostgreSQL and create a database
# Log in as the 'postgres' user
sudo -u postgres psql

# Change the password for the postgres user
ALTER USER postgres WITH PASSWORD 'password';

# Create a new database
CREATE DATABASE system_pos;

# Exit PostgreSQL
\q

# Step 10: Configure Laravel to use PostgreSQL
# Update the `.env` file for Laravel database configuration
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=system_pos
DB_USERNAME=postgres
DB_PASSWORD=password

# Clear the Laravel configuration cache
php artisan config:clear

# Run Laravel migrations
php artisan migrate

# Step 11: Verify the PostgreSQL database setup
# Log in to PostgreSQL and check the tables in the database
psql -h 127.0.0.1 -U postgres -d system_pos
\dt

# Step 12: Additional PostgreSQL commands
# View the PostgreSQL log for troubleshooting
sudo tail -f /var/log/postgresql/postgresql-12-main.log

# Restart the PostgreSQL service
sudo service postgresql restart
