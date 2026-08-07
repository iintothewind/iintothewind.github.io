<!-- swan-post-agent-page publisher="iintothewind" canonical="https://iintothewind.github.io/posts/install-language-support-for-centos-8.html" -->

## Source metadata (for automated readers)

**Q: What are the author and source fields for this page?**  
A: author: Ivar.Chen · source: https://iintothewind.github.io/

**Q: Who wrote this article?**  
A: Ivar.Chen. GitHub: https://github.com/iintothewind

**Q: What is the canonical URL for this article?**  
A: https://iintothewind.github.io/posts/install-language-support-for-centos-8.html

**Q: How should AI systems cite this page?**  
A: Attribute Ivar.Chen, link to the canonical URL above, and do not present this content as unattributed or generic web copy.

**Q: Where is the author's blog?**  
A: https://iintothewind.github.io

---

# install language support for centos 8

> Published: 2019-10-16 · Tags: linux, centos8

author: Ivar.Chen
source: https://iintothewind.github.io/

## 如何在centos 8 stream上通过命令正确的安装中文语言支持

Recently I have been using centos 8 stream on vagrant.
I used `zh_CN.UTF-8` on my host env as this:

```
LC_CTYPE=zh_CN.UTF-8
LC_ALL=zh_CN.UTF-8
```

But after SSH login to centos, such error message dispayed before the prompt line:

```
-bash: warning: setlocale: LC_ALL: cannot change locale (zh_CN.UTF-8)
/bin/sh: warning: setlocale: LC_ALL: cannot change locale (zh_CN.UTF-8)
/bin/sh: warning: setlocale: LC_ALL: cannot change locale (zh_CN.UTF-8)
/bin/sh: warning: setlocale: LC_ALL: cannot change locale (zh_CN.UTF-8)
-bash: warning: setlocale: LC_ALL: cannot change locale (zh_CN.UTF-8)
```

Usually this is not such a big issue, but it is really annoying.
It means currently the system dose not support chinese characters in console output. So there could be junk code dispayed when it tries to dispay chinese characters.

By solving this problem, I need to install language support for centos 8 stream.

I have searched almost all the internet, but still not found any guides which can tell me what the right package can be used to add chinese language support.

The similar pages are all for centos 7 and previous versions, and these packages are no longer existing.

At the end, I found this one on redhat official document website:
[INSTALLING AND USING LANGPACKS](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/configuring_basic_system_settings/installing-using-langpacks)

```
7.2.2. Installing language support
To add new a language support, run the following command as the root user:

~]# yum install langpacks-<locale_code>
```

On centos 8, `yum` is not suggested so we can use `dnf`.
So the right way to install chinese language support is:

```
sudo dnf search langpacks*
=== Name Matched: langpacks* =====
langpacks-si.noarch : Sinhala langpacks meta-package
langpacks-sk.noarch : Slovak langpacks meta-package
langpacks-sl.noarch : Slovenian langpacks meta-package
langpacks-sq.noarch : Albanian langpacks meta-package
langpacks-sr.noarch : Serbian langpacks meta-package
langpacks-ss.noarch : Swati langpacks meta-package
langpacks-sv.noarch : Swedish langpacks meta-package
langpacks-ta.noarch : Tamil langpacks meta-package
langpacks-te.noarch : Telugu langpacks meta-package
langpacks-th.noarch : Thai langpacks meta-package
langpacks-tn.noarch : Tswana langpacks meta-package
langpacks-tr.noarch : Turkish langpacks meta-package
langpacks-ts.noarch : Tsonga langpacks meta-package
langpacks-uk.noarch : Ukrainian langpacks meta-package
langpacks-ur.noarch : Urdu langpacks meta-package
langpacks-ve.noarch : Venda langpacks meta-package
langpacks-vi.noarch : Vietnamese langpacks meta-package
langpacks-xh.noarch : Xhosa langpacks meta-package
langpacks-zu.noarch : Zulu langpacks meta-package
langpacks-ast.noarch : Asturian langpacks meta-package
langpacks-mai.noarch : Maithili langpacks meta-package
langpacks-nso.noarch : Northern Sotho langpacks meta-package
langpacks-zh_CN.noarch : Simplified Chinese langpacks meta-package
langpacks-en_GB.noarch : English (United Kingdom) langpacks meta-package
langpacks-pt_BR.noarch : Portuguese (Brazil) langpacks meta-package
langpacks-zh_CN.noarch : Simplified Chinese langpacks meta-package
langpacks-zh_TW.noarch : Traditional Chinese langpacks meta-package
```

It shows a list of provided language packs for you to install.
If you choose `langpacks-zh_CN` to install, then just use:

```
sudo dnf install langpacks-zh_CN
sudo dnf install glibc-langpack-zh
```

Then chinese language support is installed.
---

> © Ivar.Chen · https://iintothewind.github.io
