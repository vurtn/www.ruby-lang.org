---
layout: news_post
title: "Ruby 3.0.4 est disponible"
author: "nagachika and mame"
translator: "Kevin Rosaz"
date: 2022-04-12 12:00:00 +0000
lang: fr
---

Ruby 3.0.4 est disponible.

Cette version contient des corrections concernant des problèmes de sécurité.
Merci de regarder les sujets suivants pour plus de détails.

* [CVE-2022-28738 : Double free dans la compilation de Regexp]({%link fr/news/_posts/2022-04-12-double-free-in-regexp-compilation-cve-2022-28738.md %})
* [CVE-2022-28739 : Dépassement de mémoire tampon lors de la conversion d'un String en Float]({%link fr/news/_posts/2022-04-12-buffer-overrun-in-string-to-float-cve-2022-28739.md %})

Voir les [logs de commit](https://github.com/ruby/ruby/compare/v3_0_3...v3_0_4) pour de plus amples informations.

## Téléchargement

{% assign release = site.data.releases | where: "version", "3.0.4" | first %}

* <{{ release.url.gz }}>

      SIZE: {{ release.size.gz }}
      SHA1: {{ release.sha1.gz }}
      SHA256: {{ release.sha256.gz }}
      SHA512: {{ release.sha512.gz }}

* <{{ release.url.xz }}>

      SIZE: {{ release.size.xz }}
      SHA1: {{ release.sha1.xz }}
      SHA256: {{ release.sha256.xz }}
      SHA512: {{ release.sha512.xz }}

* <{{ release.url.zip }}>

      SIZE: {{ release.size.zip }}
      SHA1: {{ release.sha1.zip }}
      SHA256: {{ release.sha256.zip }}
      SHA512: {{ release.sha512.zip }}

## Commentaire de version

Merci aux contributeurs, développeurs et utilisateurs qui, en reportant les bugs, nous ont permis de faire cette version.
