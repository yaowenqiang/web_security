# Cross-site Scripting: CSS

+ Stored XSS - Code that executes attacker's script in persisted
+ Reflected XSS - Transient response from server causes script to execut [i.e, a validation error]
+ DOM Based XSS - No server involvement is required(i.e, pass code in vai query Params)
+ Blind XSS - Exploits vunlnerability in another app (i.e, logreader), that attacher can't see or access under normal neams

## Location of XSS

+ user-generated rich text (i.e, WYSIWYG)
+ Embedded content
+ Anywhere users have control over a URL
+ Anywhere user input reflected back (i.e, "couldn't find _")
+ element.innerHTML = ?

> https://beefproject.com
> https://github.com/byt3bl33d3r/MITMf

## XSS Defenses: Content Security Policy(CSP)

> Content-Security-Policy: script-src 'self' https://www.xxx.com font-src: https://fonts.googleapis.com

### Selection of Useful CSP Directives

+ child-src: child execution contexts(frames, workers)
+ connect-src: what you can connect to (fetch, Websocket, EventSource)
+ form-action: where you can <form> submit to
+ img-src, media-src, object-src: where you can get images, media, flash from
+ style-src: where extenal stylesheets can come from
+ upgrade-insecure-requests: upgrades HTTP to HTTPS
+ default-src: fallback, for when specific directive isn't provided

### keywords can use along side sources

+ 'none' : no sources allowed
+ 'self' : current origin
+ 'unsafe-inline' : allows inline javascripts & css
+ 'unsafe-eval': allows eval()

> Cryptographic nonces
+ script-src "sha256-"

## XSS Attachments

> PDF  with trojan
> image with html contents

# CSRF Cross-Site Request Forgery


> Takes advantage of the fact that cookies(or Basic Authentication credentials) are passed along with requests)

  < image src="" />


## CSRF TOken
## Validate Request Origin
## Host and X-Forward-Host if behind a proxy
## CORS(Cross-Origin Resource Sharing)

> a preflight OPTIONS request gives server a chance to indicate what's allowed
> Main request follows

# clickjacking

+ A "UI" redress attach"
+ Can be used to capture keystrokes as well

## clickjacking Defenses: Modern Browsers

+ X-Frame-Options:
  + X-Frame-Options: DENY
  + X-Frame-Options: SAMEORIGIN
  + X-Frame-Options: ALLOW-FROM: https://localhost/

+ Chrome/Safari don't respect alllowfrom ,Use frame-ancestors CSP directive instead
+ this applies to the TOP LEVEL frame

# Thirdy party Assets

> subresource integrity

# Man-in-the-Middle

> wifi PINEAPPLE
> wifi antenna
> ominous box for wifi pineapple
> femtocell
> snyk


## OpenSSL

### Generate a private key

> openssl genrsa -aes128 \
    -out my-private.key 2048

### Generate a public key from private key

> openssl rsa -pubout \
    -in my-private-key \
    -out my-public.key

### Make a new Certificate Signing Request

> openssl req -new \
    -key my-private.key \
    =out my-request.csr

### Sign the certificate with your private key

> openssl x509 -req -days 3\
    -in my-request.csr \
    =signkey my-private-key \
    -out my-certificate.crt

# HTTPS downgrade

> Content-Security-Policy: upgrade-insecure-requests
+ Browser plugins attempt a "secure upgrade" whereever possible
+ https everywhere(browser plugin)

> Server Name Indication

Defending with Bad Certificate

> Strict-transport-Security: max-age=31536000; includeSubdomains

> Add your domain to HSTS Preload list: https://hstspreload.org/


HTTP Response header informs browsers of what a public-key should look like
> Public-Key-Pins: ping-sha256=""; max-age=31436000; includeSubDomains; report-uri="uri"

For the specified amount of time, browsers will continue to assert that the certificate for your domain matches the pin-sha256 value
The pin value is known as a Public Key Fingerprint

