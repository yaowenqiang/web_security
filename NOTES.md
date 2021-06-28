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
