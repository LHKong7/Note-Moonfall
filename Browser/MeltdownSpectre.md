# Meltdown / Spectre



Meltdown : reading kernel memory from user Space

Spectre: Exploit Speculative execution



If you are a **web developer**, the [Chrome team advises](https://www.chromium.org/Home/chromium-security/ssca):

- Where possible, prevent cookies from entering the renderer process' memory by using the `SameSite` and `HTTPOnly` cookie attributes, and by avoiding reading from `document.cookie`.
- Make sure your MIME types are correct and specify an `X-Content-Type-Options: nosniff` header for any URLs with user-specific or sensitive content, to get the most out of [Cross-Origin Read Blocking](https://developer.chrome.com/web/updates/2018/07/site-isolation#corb) for users who have Site Isolation enabled.
- Enable [Site Isolation](https://www.chromium.org/Home/chromium-security/site-isolation) and [let the Chrome team know](http://crbug.com/new) if it causes problems for your site.





Both Meltdown and Spectre potentially allow a process to read memory that it is not supposed to be able to. Sometimes, multiple documents from different sites can end up sharing a process in Chrome. This can happen when one has opened the other using `window.open`, or `<a href="..." target="_blank">`, or iframes. If a website contains user-specific data, there is a chance that another site could use these new vulnerabilities to read that user data.





**Efforts the Chrome and V8 Engineering team is deploying to mitigate threat**:

- Site Isolation

- Cross-Site Document Blocking

- SameSite cookies

  Cookies typically get sent for all requests to the website that sets the cookie — even if the request is made by a third party using an `<img>` tag. SameSite cookies are a new attribute that specify that a cookie should only be attached to a request that originates from the same site, hence the name.

- HTTPOnly and document.cookie

- open External Links Using `rel="noopener"`

- High-resolution timers

  To exploit Meltdown or Spectre, an attacker needs to measure how long it takes to read a certain value from memory. For this, a reliable and accurate timer is needed.

  `performance.now()` 

  `SharedArrayBuffer`

- V8