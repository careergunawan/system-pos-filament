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
