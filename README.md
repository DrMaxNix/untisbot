# Untisbot
Improved mail notifications for Untis



## Setup Instructions
Install php 8.2:
```console
# apt install lsb-release ca-certificates apt-transport-https software-properties-common gnupg2
# echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/sury-php.list
# wget -qO - https://packages.sury.org/php/apt.gpg | sudo apt-key add -
# apt update
# apt install php8.2 php8.2-curl
```

Clone git repository:
```console
# cd /opt
# git clone https://git.tjdev.de/DrMaxNix/untisbot.git
# cd untisbot
```

Install PHPMailer Library:
```console
# git clone https://github.com/PHPMailer/PHPMailer --branch v6.8.0
```

Create untisbot user:
```console
# useradd -s /bin/bash untisbot
```

Set permissions on daemon file:
```console
# chown :untisbot untisbotd
# chmod 654 untisbotd
```

Set up config file:
```console
# mkdir /etc/untisbot
# cp untisbot.template.ini /etc/untisbot/untisbot.ini
# chown :untisbot /etc/untisbot/untisbot.ini
# chmod 640 /etc/untisbot/untisbot.ini
```

Edit config to your needs:
```console
# nano /etc/untisbot/untisbot.ini
```

Install as systemd service:
```console
# ln -s /opt/untisbot/untisbot.service /etc/systemd/system/untisbot.service
# systemctl daemon-reload
# systemctl enable untisbot.service
# systemctl start untisbot.service
# systemctl status untisbot.service
```
