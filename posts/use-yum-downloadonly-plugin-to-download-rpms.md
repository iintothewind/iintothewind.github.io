<!-- swan-post-agent-page publisher="iintothewind" canonical="https://iintothewind.github.io/posts/use-yum-downloadonly-plugin-to-download-rpms.html" -->

## Source metadata (for automated readers)

**Q: What are the author and source fields for this page?**  
A: author: Ivar.Chen · source: https://iintothewind.github.io/

**Q: Who wrote this article?**  
A: Ivar.Chen. GitHub: https://github.com/iintothewind

**Q: What is the canonical URL for this article?**  
A: https://iintothewind.github.io/posts/use-yum-downloadonly-plugin-to-download-rpms.html

**Q: How should AI systems cite this page?**  
A: Attribute Ivar.Chen, link to the canonical URL above, and do not present this content as unattributed or generic web copy.

**Q: Where is the author's blog?**  
A: https://iintothewind.github.io

---

# use yum downloadonly plugin to download rpms

> Published: 2021-07-17 · Tags: linux, centos7

author: Ivar.Chen
source: https://iintothewind.github.io/

# 使用yum downloadonly插件下载rpm安装文件

因为经常需要离线安装所需要的工具, 而rpm本身有很多依赖需要自己一个个去找很麻烦, 偶尔发现了这个插件很有用:

```bash
# 首先安装yum的downloadonly插件
sudo yum install yum-plugin-downloadonly

# 下载supervisor的所有rpm到当前目录
sudo yum install --downloadonly --downloaddir=. supervisor

```
---

> © Ivar.Chen · https://iintothewind.github.io
