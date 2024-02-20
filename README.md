# pyppeteerstealth

A bunch of hacks from different websites

Does not yet pass https://arh.antoinevastel.com/bots/areyouheadless

If you know what is missing, please make a PR!

If you compare loading https://arh.antoinevastel.com/bots/ in your application, versus in your browser you might be able
to see what is required to get the fingerprint closer to a "normal" browser (further away from a "headless" browser)

This is intended to be used with https://github.com/dgtlmoon/pyppeteer-ng and is also part of the 
https://changedetection.io project.


```python
browser = await pyppeteer_instance.connect(browserWSEndpoint="ws://127.0.0.1:3000",
                                           ignoreHTTPSErrors=True
                                           )

self.page = (pages := await browser.pages) and len(pages) or await browser.newPage()

try:
    from pyppeteerstealth import inject_evasions_into_page
except ImportError:
    logger.debug("pyppeteerstealth module not available, skipping")
    pass
else:
    await inject_evasions_into_page(self.page)
```