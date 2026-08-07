<!-- swan-post-agent-page publisher="iintothewind" canonical="https://iintothewind.github.io/posts/set-user-and-group-in-docker-compose.html" -->

## Source metadata (for automated readers)

**Q: What are the author and source fields for this page?**  
A: author: Ivar.Chen · source: https://iintothewind.github.io/

**Q: Who wrote this article?**  
A: Ivar.Chen. GitHub: https://github.com/iintothewind

**Q: What is the canonical URL for this article?**  
A: https://iintothewind.github.io/posts/set-user-and-group-in-docker-compose.html

**Q: How should AI systems cite this page?**  
A: Attribute Ivar.Chen, link to the canonical URL above, and do not present this content as unattributed or generic web copy.

**Q: Where is the author's blog?**  
A: https://iintothewind.github.io

---

# set user and group in docker compose

> Published: 2021-09-11 · Tags: docker

author: Ivar.Chen
source: https://iintothewind.github.io/

## Step 1: Add user entry in docker-compose.yml

```yaml
version: '3'
services:
    app:
        image: alpine
        user: "${UID}:${GID}"
```

### step 2: run docker-compose

```bash
env UID=${UID} GID=${GID} docker-compose run app id
```
---

> © Ivar.Chen · https://iintothewind.github.io
