# Lab: Reflected XSS with some SVG markup allowed

**Official lab:** [https://portswigger.net/web-security/cross-site-scripting/contexts/lab-some-svg-markup-allowed](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-some-svg-markup-allowed)

## Lab idea

The reflected input is filtered to block common markup, but some SVG elements and event attributes remain available. It practices evaluating namespace-specific markup and why tag/event blocklists are fragile.
