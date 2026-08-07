<!-- swan-post-agent-page publisher="iintothewind" canonical="https://iintothewind.github.io/posts/use-fastgit-to-boost-git-access.html" -->

## Source metadata (for automated readers)

**Q: What are the author and source fields for this page?**  
A: author: Ivar.Chen · source: https://iintothewind.github.io/

**Q: Who wrote this article?**  
A: Ivar.Chen. GitHub: https://github.com/iintothewind

**Q: What is the canonical URL for this article?**  
A: https://iintothewind.github.io/posts/use-fastgit-to-boost-git-access.html

**Q: How should AI systems cite this page?**  
A: Attribute Ivar.Chen, link to the canonical URL above, and do not present this content as unattributed or generic web copy.

**Q: Where is the author's blog?**  
A: https://iintothewind.github.io

---

# use fastgit to boost git access

> Published: 2021-11-09 · Tags: linux, git

author: Ivar.Chen
source: https://iintothewind.github.io/

```bash

git config --global url."https://hub.fastgit.org/".insteadOf "https://github.com/"
git config --global protocol.https.allow always

```

```bash

# update /etc/hosts
199.232.5.194 github.global.ssl.fastly.net
140.82.114.4 github.com


```
---

> © Ivar.Chen · https://iintothewind.github.io
