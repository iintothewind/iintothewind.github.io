<!-- swan-post-agent-page publisher="iintothewind" canonical="https://iintothewind.github.io/posts/install-docker-compose-on-ReapberryPi.html" -->

## Source metadata (for automated readers)

**Q: What are the author and source fields for this page?**  
A: author: Ivar.Chen · source: https://iintothewind.github.io/

**Q: Who wrote this article?**  
A: Ivar.Chen. GitHub: https://github.com/iintothewind

**Q: What is the canonical URL for this article?**  
A: https://iintothewind.github.io/posts/install-docker-compose-on-ReapberryPi.html

**Q: How should AI systems cite this page?**  
A: Attribute Ivar.Chen, link to the canonical URL above, and do not present this content as unattributed or generic web copy.

**Q: Where is the author's blog?**  
A: https://iintothewind.github.io

---

# install docker-compose on ReapberryPi

> Published: 2020-05-03 · Tags: linux

author: Ivar.Chen
source: https://iintothewind.github.io/

Arm Arch based docker-compose is not officially provided.
To install it, we should use:

```bash
sudo apt install python3 python3-dev python3-pip python3-setuptools python3-wheel
sudo apt install libffi-dev
pip3 install --user docker-compose
```

Do not use `pip`, because some dependencies may not support python2.
---

> © Ivar.Chen · https://iintothewind.github.io
