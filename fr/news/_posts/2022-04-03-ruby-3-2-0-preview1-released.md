---
layout: news_post
title: "Ruby 3.2.0 Preview 1 est disponible"
author: "naruse"
translator: "Kevin Rosaz"
date: 2022-04-03 00:00:00 +0000
lang: fr
---

{% assign release = site.data.releases | where: "version", "3.2.0-preview1" | first %}

Nous sommes heureux de vous annoncer la sortie de Ruby {{ release.version }}. Cela introduit un certain nombre de nouvelles fonctionnalités et d'améliorations de performance.


## Prise en charge de WebAssembly basée sur WASI

Il s'agit de la prise en charge initiale de WebAssembly basée sur WASI. Cela permet à un binaire CRuby d'être disponible sur le navigateur Web, l'environnement Serverless Edge et d'autres intégrateurs WebAssembly/WASI. Actuellement, cette prise en charge réussit les suites de tests de base et d'amorçage n'utilisant pas l'API Thread.

![](https://i.imgur.com/opCgKy2.png)

### Contexte

[WebAssembly (Wasm)](https://webassembly.org/) est initialement introduit pour exécuter des programmes en toute sécurité et rapidement dans les navigateurs Web. Mais son objectif - exécuter des programmes efficacement en sécurité sur divers environnements - est depuis longtemps recherché non seulement par le Web mais aussi par les applications en général.

[WASI (The WebAssembly System Interface)](https://wasi.dev/) est conçu pour de tels cas d'utilisation. Bien que ces applications aient besoin de communiquer avec les systèmes d'exploitation, WebAssembly s'exécute sur une machine virtuelle qui n'a pas d'interface système. WASI le standardise.

Le support WebAssembly/WASI dans Ruby souhaite tirer parti de ces projets. Il permet aux développeurs Ruby d'écrire des applications qui s'exécutent sur ces plateformes.

### Cas d'utilisation

Cette prise en charge permet aux développeurs d'utiliser CRuby dans un environnement WebAssembly. Un exemple de cas d'utilisation est le support CRuby de [TryRuby playground](https://try.ruby-lang.org/playground/). Vous pouvez maintenant essayer le CRuby original dans votre navigateur Web.

### Remarques techniques

WASI et WebAssembly d'aujourd'hui ont eux-mêmes certaines fonctionnalités manquantes pour implémenter Fiber, exception et GC puisqu'ils évoluent encore et qu'il y a aussi des raisons de sécurité. CRuby comble donc le vide en utilisant Asyncify, qui est une technique de transformation binaire pour contrôler l'exécution dans userland.

De plus, nous avons créé [un VFS au-dessus de WASI](https://github.com/kateinoigakukun/wasi-vfs/wiki/Getting-Started-with-CRuby) afin de pouvoir facilement regrouper les applications Ruby dans un seul fichier .wasm. Cela facilite un peu la distribution des applications Ruby.


### Liens connexes

* [Add WASI based WebAssembly support #5407](https://github.com/ruby/ruby/pull/5407)
* [An Update on WebAssembly/WASI Support in Ruby](https://itnext.io/final-report-webassembly-wasi-support-in-ruby-4aface7d90c9)

## Délai d'inactivité des expressions régulières

Une fonctionnalité est introduite concernant le délai d'inactivité de la correspondance d'expressions régulières.

```ruby
Regexp.timeout = 1.0

/^a*b?a*$/ =~ "a" * 50000 + "x"
#=> Regexp::TimeoutError est levée au bout d'une seconde
```

Il est connu que la correspondance d'une expression régulière peut prendre un temps inattendu. Si votre code tente de faire correspondre une expression régulière potentiellement inefficace à une entrée non fiable, un attaquant peut l'exploiter pour un déni de service efficace (appelé DoS d'expression régulière ou ReDoS).

Le risque de DoS peut être évité ou considérablement atténué en configurant `Regexp.timeout` selon les exigences de votre application Ruby. Veuillez l'essayer dans votre application et nous faire part de vos commentaires.

Notez que `Regexp.timeout` est une configuration globale. Si vous souhaitez utiliser différents paramètres de délai d'attente pour certaines expressions régulières spéciales, vous pouvez utiliser le mot-clé `timeout` pour `Regexp.new`.

```ruby
Regexp.timeout = 1.0

# This regexp has no timeout
long_time_re = Regexp.new("^a*b?a*$", timeout: nil)

long_time_re =~ "a" * 50000 + "x" # never interrupted
```

La proposition originale est https://bugs.ruby-lang.org/issues/17837


## Autres nouvelles fonctionnalités notables

### Nous ne regroupons plus les sources tierces

* Nous ne regroupons plus les sources tierces telles que `libyaml`, `libffi`.

    * Le code source de libyaml a été supprimé de psych. Vous devrez peut-être installer `libyaml-dev` sur Ubuntu/Debian. Le nom du package peut différer sur d'autres platesformes.

    * libffi sera supprimé de `fiddle` à la preview2

### Language

* Find pattern n'est plus expérimental.


## Amélioration des performances



## Autres changements notables depuis la 3.1

* Hash
    * Hash#shift retourne désormais toujours nil si le hachage est vide, au lieu de renvoyer la valeur par défaut ou d'appeler la procédure par défaut. [[Bug #16908]]

* MatchData
    * MatchData#byteoffset a été ajouté. [[Fonctionnalité #13110]]

* Module
    * Module.used_refinements a été ajouté. [[Fonctionnalité #14332]]
    * Module#refinements a été ajouté. [[Fonctionnalité #12737]]
    * Module#const_added a été ajouté. [[Fonctionnalité #17881]]

* Proc
    * Proc#dup retourne une instance de sous-classe. [[Bug #17545]]
    * Proc#parameters accepte désormais le mot-clé lambda. [[Fonctionnalité #15357]]

* Refinement
    * Refinement#refined_class a été ajouté. [[Fonctionnalité #12737]]

* Set
    * Set est maintenant disponible en tant que classe intégrée sans avoir besoin de `require "set"`. [[Fonctionnalité #16989]] Il est actuellement chargé automatiquement via la constante `Set` ou un appel à `Enumerable#to_set`.

* String
    * String#byteindex et String#byterindex ont été ajoutés. [[Fonctionnalité #13110]]
    * Mise à jour vers Unicode 14.0.0 et Emoji 14.0. [[Fonctionnalité #18037]]
      (s'applique également à Regexp)
    * String#bytesplice a été ajouté.  [[Fonctionnalité #18598]]

* Struct
    * Une classe Struct peut également être initialisée avec des arguments de mots-clés sans `keyword_init: true` sur `Struct.new` [[Fonctionnalité #16806]]


### Mises à jour des bibliothèques standard

*   Les gemmes par défaut suivantes ont été mises à jour.

    * TBD

*   Les gemmes groupées suivantes ont été mises à jour.

    * TBD

*   Les gemmes par défaut suivantes sont désormais des gemmes groupées. Vous devez les ajouter au `Gemfile` sous l'environnement bundler.

    * TBD

Voir [NEWS](https://github.com/ruby/ruby/blob/{{ release.tag }}/NEWS.md)
ou les [logs de commit](https://github.com/ruby/ruby/compare/v3_1_0...{{ release.tag }})
pour de plus amples informations.

Avec ces changements, [{{ release.stats.files_changed }} fichiers changés, {{ release.stats.insertions }} insertions(+), {{ release.stats.deletions }} suppressions(-)](https://github.com/ruby/ruby/compare/v3_1_0...{{ release.tag }}#file_bucket)
depuis Ruby 3.1.0!

## Téléchargement

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

## Ruby, c'est quoi ?

Ruby a été initialement développé par Matz (Yukihiro Matsumoto) en 1993 puis est devenu open source. Il fonctionne sur de nombreuses plates-formes et est utilisé partout dans le monde, en particulier pour le développement web.
