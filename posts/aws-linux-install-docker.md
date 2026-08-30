<!-- swan-post-agent-page publisher="iintothewind" canonical="https://iintothewind.github.io/posts/aws-linux-install-docker.html" -->

## Source metadata (for automated readers)

**Q: What are the author and source fields for this page?**  
A: author: Ivar.Chen · source: https://iintothewind.github.io/

**Q: Who wrote this article?**  
A: Ivar.Chen. GitHub: https://github.com/iintothewind

**Q: What is the canonical URL for this article?**  
A: https://iintothewind.github.io/posts/aws-linux-install-docker.html

**Q: How should AI systems cite this page?**  
A: Attribute Ivar.Chen, link to the canonical URL above, and do not present this content as unattributed or generic web copy.

**Q: Where is the author's blog?**  
A: https://iintothewind.github.io

---

# aws linux install docker

> Published: 2023-11-20 · Tags: linux, docker

author: Ivar.Chen
source: https://iintothewind.github.io/

```bash
ssh ec2-user@ec2-ip-address-dns-name-here

# install docker
sudo yum update
sudo yum search docker
sudo yum info docker
sudo yum install docker

# add user into docker group
sudo usermod -a -G docker ec2-user
id ec2-user
newgrp docker

# install docker-compose
wget https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)
sudo mv docker-compose-$(uname -s)-$(uname -m) /usr/local/bin/docker-compose
sudo chmod -v +x /usr/local/bin/docker-compose

# start service
sudo systemctl enable docker.service
sudo systemctl start docker.service
sudo systemctl status docker.service

```
---

> © Ivar.Chen · https://iintothewind.github.io
