# Code Quality Pack

A collection of libraries you need to run behat tests on Sylius plugin or app

```bash
$ composer require --dev setono/sylius-behat-pack
```

## Preparing environment for testing with JS enabled

* Chromedriver

    https://sites.google.com/a/chromium.org/chromedriver/downloads

    ```bash
    # platform options: linux32, linux64, mac64, win32
    PLATFORM=mac64
    VERSION=$(curl http://chromedriver.storage.googleapis.com/LATEST_RELEASE)
    curl http://chromedriver.storage.googleapis.com/$VERSION/chromedriver_$PLATFORM.zip
    unzip -o chromedriver.zip
    chmod +x chromedriver
    rm chromedriver.zip
    ./chromedriver > /dev/null 2>&1 &
    ```

* Selenium

    ```bash
    curl http://selenium-release.storage.googleapis.com/3.4/selenium-server-standalone-3.4.0.jar > selenium.jar
    java -Dwebdriver.chrome.driver=chromedriver -jar selenium.jar > /dev/null 2>&1 &
    ```

* Run weserver with test environment

    ```bash
    (cd tests/Application && APP_ENV=test symfony serve 127.0.0.1:8080 > /dev/null 2>&1 &)
    ```
