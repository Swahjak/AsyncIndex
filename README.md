AsyncIndex
==========

Topper:
- run it /bin/sh /home/pooltopp/staging_html/cron.sh shell/hackathon_async_index.php >> /home/pooltopp/staging_html/var/log/cronAsyncIndex.log 2>&1

Zookal adaptions:
- run it `*/15 * * * * /bin/sh htdocs/cron.sh shell/hackathon_async_index.php >> var/cronAsyncIndex.log 2>&1` and
not via normal Magento cronjob



License: MIT

Features
--------

* Schedule Reindex from Backend (put entry in cron_schedule) and reindex via Cron
* Reindex partially (only needed parts) from shell
* Automatic background reindexing with configurable event count and schedule

Installation Instructions
-------------------------

### Via modman

- Install [modman](https://github.com/colinmollenhour/modman)
- Use the command from your Magento installation folder: `modman clone https://github.com/magento-hackathon/Hackathon_AsyncIndex/`

### Via composer
- Install [composer](http://getcomposer.org/download/)
- Install [Magento Composer](https://github.com/magento-hackathon/magento-composer-installer)
- Create a composer.json into your project like the following sample:

```json
{
    ...
    "require": {
        "magento-hackathon/async-index":"*"
    },
    "repositories": [
	    {
            "type": "composer",
            "url": "http://packages.firegento.com"
        }
    ],
    "extra":{
        "magento-root-dir": "./"
    }
}
```

- Then from your `composer.json` folder: `php composer.phar install` or `composer install`

### Manually
- You can copy the files from the folders of this repository to the same folders of your installation


### Installation in ALL CASES
* Clear the cache, logout from the admin panel and then login again.

Uninstallation
--------------
* Remove all extension files from your Magento installation
* Via modman: `modman remove Hackathon_AsyncIndex`
* Via composer, remove the line of your composer.json related to `magento-hackathon/hackathon_asyncindex`


Configuration
-------------

You can configure the automatic background indexing from: `System -> Configuration -> System -> Asynchronous Indexing`

Available options are:

* `Enable Automatic Indexing` - Default: `Yes`
* `Async Indexing Crontab` - Default: `*/5 * * * *`
* `Events Limit` - Default: `200` - This limit is per process, keep it at a sensible number for large catalogs

