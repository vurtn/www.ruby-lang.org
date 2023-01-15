---
layout: news_post
title: "Ruby 3.0.5 est disponible"
author: "usa"
translator: "Kevin Rosaz"
date: 2022-11-24 12:00:00 +0000
lang: fr
---

Ruby 3.0.5 est disponible.

Cette version contient des corrections concernant des problèmes de sécurité.
Merci de regarder les sujets suivants pour plus de détails.

* [CVE-2021-33621: HTTP response splitting in CGI]({%link fr/news/_posts/2022-11-22-http-response-splitting-in-cgi-cve-2021-33621.md %})

Cette version inclut également la résolution de bugs.
Voir les [logs de commit](https://github.com/ruby/ruby/compare/v3_0_4...v3_0_5) pour de plus amples informations.

## Téléchargement

{% assign release = site.data.releases | where: "version", "3.0.5" | first %}

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

La maintenance de Ruby 3.0, incluant cette version, est basée sur l' "Agreement for the Ruby stable version" de la Ruby Association.
