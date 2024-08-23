FROM mcr.microsoft.com/devcontainers/php:1-8.3-bullseye

# Install PostgresSQL client
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get install -y postgresql-client libicu-dev libpq-dev \ 
    && apt-get clean -y && rm -rf /var/lib/apt/lists/*

RUN . $NVM_DIR/nvm.sh \
    && nvm install node \
    && nvm use default

RUN curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | bash \
    && apt install symfony-cli

# Install php-pgsql driver
RUN docker-php-ext-install pgsql pdo pdo_pgsql intl opcache

COPY php/php.ini /usr/local/etc/php/php.ini

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1