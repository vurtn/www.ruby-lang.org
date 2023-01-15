---
layout: news_post
title: "Ruby 3.1.3 est disponible"
author: "nagachika"
translator: "Kevin Rosaz"
date: 2022-11-24 12:00:00 +0000
lang: fr
---

Ruby 3.1.3 est disponible.

Cette version contient des corrections concernant des problèmes de sécurité.
Merci de regarder les sujets suivants pour plus de détails.

* [CVE-2021-33621: HTTP response splitting in CGI]({%link fr/news/_posts/2022-11-22-http-response-splitting-in-cgi-cve-2021-33621.md %})

This release also includes a fix for build failure with Xcode 14 and macOS 13 (Ventura).
Voir [le ticket associé](https://bugs.ruby-lang.org/issues/18912) afin d'avoir plus de détails.

Voir les [logs de commit](https://github.com/ruby/ruby/compare/v3_1_2...v3_1_3) pour de plus amples informations.

## Téléchargement

{% assign release = site.data.releases | where: "version", "3.1.3" | first %}

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
