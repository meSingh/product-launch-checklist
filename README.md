Product Lauch Checklist 📔 [WIP] 
------

A checklist used for all projects when going live

# 1. Front end checklist

## Page weight

- [ ]  Evaluate total weight of at least homepage
- [ ]  Open Inspector network/timeline tab to identify heavy assets
- [ ]  Check if heavy assets are cached

## Performance

- [ ]  Use the Chrome DevTools and throttle your CPU and network with 10x CPU slowdown and set the network to "Good 3G".
- [ ]  [https://github.com/thedaviddias/Front-End-Performance-Checklist](https://github.com/thedaviddias/Front-End-Performance-Checklist)

# 2. Check content (with an open console)

- [ ]  Are 404, 500 and 503 pages provided? Do they provide useful content like 'back to home', search or a navigation tree?

## Meta

- [ ]  Check page titles / descriptions
- [ ]  Test Facebook sharing. Provide og-tags if needed
- [ ]  Does Favicon load? Pin the tab in Safari to check pinned icon
- [ ]  Check domain on HeyMeta.com

    [HEY META - Website Meta Tag Check](http://www.heymeta.com/)

## Components

- [ ]  Check structured data for news, events, products,... https://search.google.com/structured-data/testing-tool/

# 4. Back end checklist

- [ ]  

# 5. Server, DNS & Services

- [ ]  Set CloudFlare and do that necessary configurations
    - [ ]  **Crypto Tab:**
        - [ ]  SSL => Flexible
        - [ ]  Always use HTTPS => YES
        - [ ]  Automatic HTTPS Rewrites => YES
    - [ ]  Firewall:
        - [ ]  Security Level => Essentially Off
- [ ]  Check SSL certificate health https://www.ssllabs.com/ssltest/
- [ ]  Try out visiting `http`, should redirect to `https`
- [ ]  Verify that all http status codes are ok with https://github.com/spatie/http-status-check
- [ ]  Scan for mixed content with https://github.com/spatie/mixed-content-scanner-cli
- [ ]  Verify Tag Manager / Analytics have been correctly set up

# 6. Open Source

- [ ]  Add a few badges : [https://forthebadge.com](https://forthebadge.com/)

# 7. SEO

- [ ]  Check site on : [https://varvy.com](https://varvy.com)

    [Varvy SEO tool and optimization guide](https://varvy.com)

# 8. Security

- [ ]  Content Security Policy 101

    [Content Security Policy 101](https://christoph-rumpel.com/2018/03/content-security-policy-101)

# 9. Services

## Google Search Console

- [ ]  Submit all www/non-www http/https variations
- [ ]  Set up non-www/www https as the preferred domain
- [ ]  Crawl > Fetch as Google > Submit to index to kickstart index

## Server

- [ ]  Are Server backups enabled?
- [ ]  Are Amazon S3 backups enabled for database?

## Github

- [ ]  Remove `develop` branch or other stale branches
- [ ]  Write a solid README : [How to write a README that rocks](https://m.dotdev.co/how-to-write-a-readme-that-rocks-bc29f279611a)
