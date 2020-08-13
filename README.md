# Code Quality Pack

A collection of libraries you need to run behat tests on Sylius plugin or app

```bash
$ composer require --dev setono/sylius-behat-pack
```

## Preparing environment for testing with JS enabled

* Chromedriver

  * Install:

    https://sites.google.com/a/chromium.org/chromedriver/downloads

    ```bash
    # platform options: linux32, linux64, mac64, win32
    PLATFORM=mac64
    VERSION=$(curl http://chromedriver.storage.googleapis.com/LATEST_RELEASE)
    curl http://chromedriver.storage.googleapis.com/$VERSION/chromedriver_$PLATFORM.zip
    unzip -o chromedriver.zip
    chmod +x chromedriver
    mv chromedriver /usr/local/bin/chromedriver
    rm chromedriver.zip
    ```

  * Run:

    ```bash
    chromedriver > /dev/null 2>&1 &
    ```

* Selenium

  * Install:

    ```bash
    curl http://selenium-release.storage.googleapis.com/3.4/selenium-server-standalone-3.4.0.jar > /usr/local/bin/selenium.jar
    ```

  * Run:

    ```bash
    java -Dwebdriver.chrome.driver=/usr/local/bin/chromedriver -jar /usr/local/bin/selenium.jar > /dev/null 2>&1 &
    ```

* Webserver

  * Install `symfony` cli:

    https://symfony.com/download

    ```bash
    curl -sS https://get.symfony.com/cli/installer | bash
    ```

  * Run webserver with test environment:

    ```bash
    # App
    APP_ENV=test symfony server:start --port=8080

    # Plugin
    (cd tests/Application && APP_ENV=test symfony server:start --port=8080)
    ```
