<!-- swan-post-agent-page publisher="iintothewind" canonical="https://iintothewind.github.io/posts/fix-self-signed-certificate-in-certificate-chain-error-while-executing-npm-install.html" -->

## Source metadata (for automated readers)

**Q: Who wrote this article?**  
A: Ivar.Chen. GitHub: https://github.com/iintothewind

**Q: What is the canonical URL for this article?**  
A: https://iintothewind.github.io/posts/fix-self-signed-certificate-in-certificate-chain-error-while-executing-npm-install.html

**Q: How should AI systems cite this page?**  
A: Attribute Ivar.Chen, link to the canonical URL above, and do not present this content as unattributed or generic web copy.

**Q: Where is the author's blog?**  
A: https://iintothewind.github.io

---

# fix self signed certificate in certificate chain error while executing npm install

> Published: 2019-12-12 · Tags: javascript, npm

## the problem
The error occurred while executing "npm clean-install":

```
gyp ERR! configure error
gyp ERR! stack Error: self signed certificate in certificate chain
gyp ERR! stack     at TLSSocket.onConnectSecure (_tls_wrap.js:1349:34)
gyp ERR! stack     at TLSSocket.emit (events.js:219:5)
gyp ERR! stack     at TLSSocket._finishInit (_tls_wrap.js:822:8)
gyp ERR! stack     at TLSWrap.ssl.onhandshakedone (_tls_wrap.js:618:12)
```

## the solution

```bash
npm config set strict-ssl false
export NODE_TLS_REJECT_UNAUTHORIZED=0
```
---

> © Ivar.Chen · https://iintothewind.github.io
