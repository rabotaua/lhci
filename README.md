# Lighthouse CI

Docker image with puppeteer preinstalled

Original can be found [here](https://github.com/GoogleChrome/lighthouse-ci/blob/master/docs/recipes/docker-client/Dockerfile)

Original docs can be found [here](https://github.com/GoogleChrome/lighthouse-ci#documentation)

# Usage example

```bash
docker run -it --rm  --cap-add=SYS_ADMIN -v $PWD:/data -w /data rabotaua/lhci lhci collect --numberOfRuns=1 --url="https://m.rabota.ua/"
```

# Auth

**script.js**

```js
module.exports = async (browser, context) => {
  const page = await browser.newPage();
  await page.goto("https://m.rabota.ua/account/login");
  await page.type("#email", "marchenko.alexandr@gmail.com");
  await page.type("#password", "*************");
  await page.click('input[type="submit"]');
  await page.waitForNavigation();
};
```

```bash
docker run -it --rm  --cap-add=SYS_ADMIN -v $PWD:/data -w /data rabotaua/lhci lhci collect --numberOfRuns=1 --url="https://m.rabota.ua/notepad/cvlist" --puppeteerScript="script.js"
```

# Reports

```bash
ls -la .lighthouseci
open .lighthouseci/lhr-*.html
```
