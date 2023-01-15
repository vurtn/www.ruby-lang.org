---
layout: news_post
title: "Ruby 2.7.6 est disponible"
author: "usa and mame"
translator: "Kevin Rosaz"
date: 2022-04-12 12:00:00 +0000
lang: fr
---

Ruby 2.7.6 est disponible.

Cette version contient des corrections concernant des problèmes de sécurité.
Merci de regarder les sujets suivants pour plus de détails.

* [CVE-2022-28739 : Dépassement de mémoire tampon lors de la conversion d'un String en Float]({%link fr/news/_posts/2022-04-12-buffer-overrun-in-string-to-float-cve-2022-28739.md %})

Cette version inclut également la résolution de bugs.
Voir les [logs de commit](https://github.com/ruby/ruby/compare/v2_7_5...v2_7_6) pour de plus amples informations.

Après cette version, ce sera la fin de la phase standard de maintenance de la
branche 2.7. Cela marquera le début de sa phase de maintance de sécurité. Cela signifie
qu'il n'y aura plus de *backports* depuis les versions plus récentes, sauf
pour les correctifs de sécurité. 

Cette phase de maintenance réduite s'achèvera dans un an, à l'issue de quoi la branche 2.7 ne sera plus officiellement supportée. 

De ce fait, nous vous recommandons de passer à Ruby 3.0 ou 3.1.

## Téléchargement

{% assign release = site.data.releases | where: "version", "2.7.6" | first %}

* <{{ release.url.bz2 }}>

      SIZE: {{ release.size.bz2 }}
      SHA1: {{ release.sha1.bz2 }}
      SHA256: {{ release.sha256.bz2 }}
      SHA512: {{ release.sha512.bz2 }}

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

Le support de la branche 2.7 est documenté et encadré par le document
*Agreement for the Ruby stable version* publié par la [*Ruby Association*](http://www.ruby.or.jp/).
