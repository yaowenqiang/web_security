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
+ 

