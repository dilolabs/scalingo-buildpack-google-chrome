# scalingo-buildpack-google-chrome

This buildpack downloads and installs (headless) Google Chrome from your choice
of release channels.

> [!IMPORTANT]
> When used with Chromedriver, the Chromedriver version (installed by a different buildpack) falls out of sync with Chrome causing build failures.
>
> **Instead, please use [Chrome for Testing buildpack](https://github.com/heroku/heroku-buildpack-chrome-for-testing)**, which installs  [matching Chrome + Chromedriver versions](https://googlechromelabs.github.io/chrome-for-testing/).

## Channels

You can choose your release channel by specifying `GOOGLE_CHROME_CHANNEL` as
a config var for your app.

Valid values are `stable`, `beta`, and `unstable`. If unspecified, the `stable`
channel will be used.

## Shims and Command Line Flags

This buildpack installs shims that always add `--headless`, `--disable-gpu`,
`--no-sandbox`, `--remote-debugging-port=9222` and `--disable-dev-shm-usage` to any `google-chrome`
command as you'll have trouble running Chrome on a Scalingo dyno otherwise.

You'll have two of these shims on your path: `google-chrome` and
`google-chrome-$GOOGLE_CHROME_CHANNEL`. They both point to the binary of
the selected channel.

## Selenium

> [!CAUTION]
> To use Selenium, do not install this buildpack.
>
> **Instead, please use [Chrome for Testing buildpack](https://github.com/heroku/heroku-buildpack-chrome-for-testing)**, which installs  [matching Chrome + Chromedriver versions](https://googlechromelabs.github.io/chrome-for-testing/).

## Special thanks

Thanks to Heroku for providing the source of this fork.