<!-- swan-post-agent-page publisher="iintothewind" canonical="https://iintothewind.github.io/posts/centos-7-install-docker.html" -->

## Source metadata (for automated readers)

**Q: What are the author and source fields for this page?**  
A: author: Ivar.Chen · source: https://iintothewind.github.io/

**Q: Who wrote this article?**  
A: Ivar.Chen. GitHub: https://github.com/iintothewind

**Q: What is the canonical URL for this article?**  
A: https://iintothewind.github.io/posts/centos-7-install-docker.html

**Q: How should AI systems cite this page?**  
A: Attribute Ivar.Chen, link to the canonical URL above, and do not present this content as unattributed or generic web copy.

**Q: Where is the author's blog?**  
A: https://iintothewind.github.io

---

# centos 7 install docker

> Published: 2021-07-26 · Tags: linux, centos7

author: Ivar.Chen
source: https://iintothewind.github.io/

```bash

sudo yum remove mariadb-libs

sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
sudo dnf config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo

sudo yum install docker-ce docker-ce-cli
sudo dnf install docker-ce docker-ce-cli

sudo vim /etc/docker/daemon.json
```


```json
{
"registry-mirrors": ["https://registry.docker-cn.com","http://hub-mirror.c.163.com"],
"live-restore": true
}
```
---

> © Ivar.Chen · https://iintothewind.github.io
