<h1 align="center">
  Product Launch Checklist
</h1>

<h4 align="center">A checklist used for all projects when going live</h4>

<p align="center">
  <a href="http://makeapullrequest.com">
    <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square" alt="PRs Welcome">
  </a>
    <a href="https://opensource.org/licenses/MIT">
    <img src="https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square" alt="Licence MIT">
  </a>
</p>

<p id="table-of-contents" align="center"><a href="#html">HTML</a> • <a href="#css">CSS</a> • <a href="#fonts">Fonts</a> • <a href="#images">Images</a> • <a href="#javascript">JavaScript</a> • <a href="#server">Server</a> • <a href="#seo--services">SEO & Services</a> • <a href="#contributing">Contributing</a></p>

---

## HTML

![html]

- [ ] **Minified HTML:** ![medium] The HTML code is minified, comments, white spaces and new lines are removed from production files.
- [ ] **Remove unnecessary comments:** ![low] Ensure that comments are removed from your pages.
- [ ] **Remove unnecessary attributes:** ![low] Type attributes like `type="text/javascript"` or `type="text/css"` are not required anymore and should be removed.

    ```html
    <!-- Before HTML5 -->
    <script type="text/javascript">
        // JavaScript code
    </script>

    <!-- Today -->
    <script>
        // JavaScript code
    </script>
    ```

- [ ] **Favicon present:** ![high] Does Favicon load? Pin the tab in Safari to check pinned icon
* 🛠 [Real Favicon Generator](https://realfavicongenerator.net)
- [ ] **Meta Title / Description Available:**  ![high] Check page titles / descriptions
- [ ] **Social Tags Present:** ![high] Test Facebook sharing. Provide og-tags if needed

* 🛠 [HEY META - Website Meta Tag Check](http://www.heymeta.com/)

**[⬆ back to top](#table-of-contents)**

## CSS

![css]

- [ ] **Minification:** ![high] All CSS files are minified, comments, white spaces and new lines are removed from production files.

    * 🛠 [cssnano: A modular minifier based on the PostCSS ecosystem.](https://cssnano.co/)


- [ ] **Concatenation:** ![medium] CSS files are concatenated in a single file *(Not always valid for HTTP/2)*.

    ```html

    <!-- Not recommended -->
    <link rel="stylesheet" href="foo.css"/>
    <link rel="stylesheet" href="bar.css"/>

    <!-- Recommended -->
    <link rel="stylesheet" href="foobar.css"/>
    ```

- [ ] **Non-blocking:** ![high] CSS files need to be non-blocking to prevent the DOM from taking time to load.

    ```html
    <link rel="preload" href="global.min.css" as="style" onload="this.rel='stylesheet'">
    <noscript><link rel="stylesheet" href="global.min.css"></noscript>
    ```

    > ⁃ You need to add the `rel` attribute with the `preload` value and add `as="style"` on the `<link>` element.

    * 🛠 [preload-webpack-plugin](https://github.com/GoogleChromeLabs/preload-webpack-plugin)


- [ ] **Unused CSS:** ![medium] Remove unused CSS selectors.

    * 🛠 [PurifyCSS](https://github.com/purifycss/purifycss)
    * 🛠 [PurgeCSS](https://github.com/FullHuman/purgecss)

**[⬆ back to top](#table-of-contents)**

## Fonts

![fonts]

* 📖 [A Book Apart, Webfont Handbook](https://abookapart.com/products/webfont-handbook)

- [ ] **Webfont formats:** ![medium] You are using WOFF2 on your web project or application.
- [ ] **Use `preconnect` to load your fonts faster:** ![medium]

    ```html
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    ```

    > ⁃ Before prefetching your webfonts, use webpagetest to evaluate your website <br>
    ⁃ Look for teal colored DNS lookups and note the host that are being requested <br>
    ⁃ Prefetch your webfonts in your `<head>` and add eventually these hostnames that you should prefetch too

    * 📖 [Faster Google Fonts with Preconnect - CDN Planet](https://www.cdnplanet.com/blog/faster-google-webfonts-preconnect/)
    * 📖 [Make Your Site Faster with Preconnect Hints | Viget](https://www.viget.com/articles/make-your-site-faster-with-preconnect-hints/)
    * 📖 [Ultimate Guide to Browser Hints: Preload, Prefetch, and Preconnect - MachMetrics Speed Blog](https://www.machmetrics.com/speed-blog/guide-to-browser-hints-preload-preconnect-prefetch/)

- [ ] **Webfont size:** ![medium] Webfont sizes don't exceed 300kb (all variants included)

 * 📖 [Font Bytes - Page Weight](https://httparchive.org/reports/page-weight#bytesFont)


**[⬆ back to top](#table-of-contents)**

## JavaScript

![javascript]

- [ ] **JS Minification:** ![high] All JavaScript files are minified, comments, white spaces and new lines are removed from production files *(still valid if using HTTP/2)*.

    * 🛠 [uglify-js - npm](https://www.npmjs.com/package/uglify-js)

* [ ] **No JavaScript inside:** ![medium] *(Only valid for website)* Avoid having multiple JavaScript codes embedded in the middle of your body. Regroup your JavaScript code inside external files or eventually in the `<head>` or at the end of your page (before `</body>`).

    > Ensure that all your files are loaded using `async` or `defer` and decide wisely the code that you will need to inject in your `<head>`.

     * 📖 [11 Tips to Optimize JavaScript and Improve Website Loading Speeds](https://www.upwork.com/hiring/development/11-tips-to-optimize-javascript-and-improve-website-loading-speeds/)

* [ ] **Non-blocking JavaScript:** ![high] JavaScript files are loaded asynchronously using `async` or deferred using `defer` attribute.

    ```html
    <!-- Defer Attribute -->
    <script defer src="foo.js"></script>

    <!-- Async Attribute -->
    <script async src="foo.js"></script>
    ```

    > ⁃ Add `async` (if the script don't rely on other scripts) or `defer` (if the script relies upon or relied upon by an async script) as an attribute to your script tag. <br>
    ⁃ If you have small scripts, maybe use inline script place above async scripts.

    * 📖 [Remove Render-Blocking JavaScript](https://developers.google.com/speed/docs/insights/BlockingJS)
    * 📖 [Defer loading JavaScript](https://varvy.com/pagespeed/defer-loading-javascript.html)

- [ ] **Check dependencies size limit:** ![low] Ensure to use wisely external libraries, most of the time, you can use a lighter library for a same functionality.

- [ ] **JavaScript Profiling:** ![medium] Check for performance problems in your JavaScript files (and CSS too).

- [ ] **Use of Service Workers:** ![medium] You are using Service Workers in your PWA to cache data or execute possible heavy tasks without impacting the user experience of your application.
   

**[⬆ back to top](#table-of-contents)**

## Server

![server-side]

- [ ] **Your website is using HTTPS:** ![high] 
- [ ] **Page weight < 1500 KB (ideally < 500 KB):** ![high] Reduce the size of your page + resources as much as you can.
- [ ] **Page load times < 3 seconds:** ![high] Reduce as much as possible your page load times to quickly deliver your content to your users.

    > Use online tools like [Page Speed Insight](https://developers.google.com/speed/pagespeed/insights/) or [WebPageTest](https://www.webpagetest.org/) to analyze what could be slowing you down and use the Front-End Performance Checklist to improve your load times.

- [ ] **Time To First Byte < 1.3 seconds:** ![high] Reduce as much as you can the time your browser waits before receiving data.

    * 📖 [What is Waiting (TTFB) in DevTools, and what to do about it](https://scaleyourcode.com/blog/article/27)

- [ ] **Minimizing HTTP requests:** ![high] Always ensure that every file requested are essential for your website or application.
- [ ] **Use a CDN to deliver your assets:** ![medium] Use a CDN to deliver faster your content over the world.

- [ ] **Set HTTP cache headers properly:** ![high] Set HTTP headers to avoid expensive number of roundtrips between your browser and the server.
 * 📖 [Using cache-control for browser caching](https://varvy.com/pagespeed/cache-control.html)

- [ ] **GZIP / Brotli compression is enabled:** ![high] Use a compression method such as Gzip or Brotli to reduce the size of your JavaScript files. With a smaller sizes file, users will be able to download the asset faster, resulting in improved performance.

 * 🛠 [Check GZIP compression](https://checkgzipcompression.com/)
 * 🛠 [Check Brotli Compression](https://tools.keycdn.com/brotli-test)
 * 📖 [Can I use... Brotli](https://caniuse.com/#feat=brotli)ssdxca


**[⬆ back to top](#table-of-contents)**



## SEO & Services

![meta]

- [ ] **Content Security:** ![low] Content Security Policy 101

* 📖 [Content Security Policy 101](https://christoph-rumpel.com/2018/03/content-security-policy-101)

- [ ] **Robots.txt:** ![high] Verify robots.txt is present and allow's all robots
- [ ] **Sitemap:** ![high] ensure that a sitemap is present and if the content is dynamic, proper functionality is there to auto update it
- [ ] **Analytics:** ![high] Verify Tag Manager / Analytics have been correctly set up
    
### Cloudflare

- [ ] ![high] Set CloudFlare and do that necessary configurations
    - [ ]  **SSL/TLS:**
        - [ ]  Your SSL/TLS encryption mode => Flexible
    - [ ]  **SSL/TLS -> Edge Certificates:**
        - [ ]  Always use HTTPS => YES
        - [ ]  Automatic HTTPS Rewrites => YES
    - [ ]  **Firewall -> Settings:**
        - [ ]  Security Level => Essentially Off


### Google Search Console

- [ ] ![low] Submit all www/non-www http/https variations
- [ ] ![low] Set up one non-www/www https as the preferred domain
- [ ] ![low] Crawl > Fetch as Google > Submit to index to kickstart index

### Bing Webmaster Tools

- [ ] ![low] Submit the site to [Bing Webmaster](https://www.bing.com/webmaster/home/) OR Import from Google

### Backups

- [ ] **Server:** ![medium] Are Server backups enabled?
- [ ] **Database:** ![medium] Are Amazon S3 backups enabled for database?

### Github

- [ ]  **Branches Cleanup:** ![low] Remove `develop` branch or other stale branches
- [ ]  **Write a solid README:** ![medium] [How to write a README that rocks](https://m.dotdev.co/how-to-write-a-readme-that-rocks-bc29f279611a)
### Twitter
- [ ] Finally, let the world know... 

**[⬆ back to top](#table-of-contents)**


---

## Contributing

**Open an issue or a pull request to suggest changes or additions.**


## License

[MIT](LICENSE)

All icons are provided by [Icons8](https://icons8.com/)

**[⬆ back to top](#table-of-contents)**

[html]: images/html.png
[css]: images/css.png
[fonts]: images/fonts.png
[images]: images/images.png
[javascript]: images/javascript.png
[server-side]: images/server-side.png
[meta]: images/meta.png

[low]: images/low.svg
[medium]: images/medium.svg
[high]: images/high.svg
