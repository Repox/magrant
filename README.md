### Authentication keys

You need authentiation keys for installing Magento via Composer.

Documentation: https://devdocs.magento.com/guides/v2.3/install-gde/prereq/connect-auth.html

Quicklink (requires account): https://marketplace.magento.com/customer/accessKeys/ 

### Installation via Composer (requires authentication keys)

Documentation: https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-sample-data-composer.html

    $ cd /vagrant
    $ composer create-project --repository=https://repo.magento.com/ magento/project-community-edition application

### Setup up Magento via CLI:

 The following installation instruction is for local development based on the Vagrant setup.

 Please review the options to ensure that settings are as you need.

     $ cd /vagrant/application
     $ bin/magento setup:install \
		--base-url=http://192.168.22.65 \
		--db-host=localhost \
		--db-name=vagrant \
		--db-user=vagrant \
		--db-password=vagrant \
		--backend-frontname=admin \
		--admin-firstname=admin \
		--admin-lastname=admin \
		--admin-email=admin@admin.com \
		--admin-user=admin \
		--admin-password=admin123 \
		--language=da_DK \
		--currency=DKK \
		--timezone=Europe/Copenhagen \
		--use-rewrites=1

### Use Redis for cache

Documentation: https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-pg-cache.html

    $ cd /vagrant/application
    $ bin/magento setup:config:set --cache-backend=redis

### Setup cron for Magento

Documentation: https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html

You can install crontabs and not worry about them:

    $ cd /vagrant/application
    $ php bin/magento cron:install


Or you can run them when needed:

    $ cd /vagrant/application
    $ php bin/magento cron:run


### Use Elasticsearch for Catalog Search

Elasticsearch 6.x is installed. Configuration is handled in the administration panel.

Nginx is configured with localhost proxy.

Documentation: https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html

