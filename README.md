# Dismissable alert

## Console error

```bash
Refused to execute inline script because it violates the following Content Security Policy directive: "script-src 'self' https://*.netlify.app 'sha512-RBYr6Ld4w1yVqaACrgrBLQfPgGhj/1jyacA74WxJ1KM6KVcSWymwrdDwb3HDcdpwiNJ5yssot1He0U9vXoQVlg==' 'sha256-aWZ3y/RxbBYKHXH0z8+8ljrHG1mSBvyzSfxSMjBSaXk=' 'sha256-vOgyKS2vkH4n5TxBJpeh9SgzrE6LVGsAeOAvEST6oCc='". Either the 'unsafe-inline' keyword, a hash ('sha256-Sz0IuK/4LfFJVp69F4UHK80xoxDZLOBPMJhPi0XZl3A='), or a nonce ('nonce-...') is required to enable inline execution.
```

## Solution

Add `sha512-RGGByJUOP98hE4wFZM78RM/3MijWJs0Tm0DbfrFhCDCXKXfDx60fii+syp5iMs3UcNX/1H4zJNgmqSejfhHrYw==` to the `Content-Security-Policy` section in `./layouts/index.headers`, like so:

```bash
/*
  Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
  X-Content-Type-Options: nosniff
  X-XSS-Protection: 1; mode=block
  Content-Security-Policy: default-src 'self'; frame-ancestors https://jamstackthemes.dev; manifest-src 'self' https://*.netlify.app; connect-src 'self' https://*.netlify.app; font-src 'self' https://*.netlify.app; img-src 'self' https://*.netlify.app data:; script-src 'self' https://*.netlify.app 'sha512-RGGByJUOP98hE4wFZM78RM/3MijWJs0Tm0DbfrFhCDCXKXfDx60fii+syp5iMs3UcNX/1H4zJNgmqSejfhHrYw==' 'sha512-RBYr6Ld4w1yVqaACrgrBLQfPgGhj/1jyacA74WxJ1KM6KVcSWymwrdDwb3HDcdpwiNJ5yssot1He0U9vXoQVlg==' 'sha256-aWZ3y/RxbBYKHXH0z8+8ljrHG1mSBvyzSfxSMjBSaXk=' 'sha256-vOgyKS2vkH4n5TxBJpeh9SgzrE6LVGsAeOAvEST6oCc='; style-src 'self' https://*.netlify.app 'unsafe-inline'
  X-Frame-Options: SAMEORIGIN
  Referrer-Policy: strict-origin
  Feature-Policy: geolocation 'self'
  Cache-Control: public, max-age=31536000
  Access-Control-Allow-Origin: *
```

## Example

- [inspiring-sherbet-2682cb.netlify.app](https://inspiring-sherbet-2682cb.netlify.app/)
