<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

En del af webstedskoden er open source, velkommen til at hjælpe med at optimere oversættelsen.

## front-end kode

* [front-end kode](https://github.com/xxai-art/web)
* [Sprogpakker til webstedet som helhed](https://github.com/xxai-art/web/tree/main/i18n)
* [Sprogpakker til login-moduler](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Hjemmeside flersproget dokumentation](https://github.com/xxai-doc)

Frontend-programmeringssproget er [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , som tilføjer nogle funktioner baseret på coffeescript-syntaksen, se [./coffee_plus.md](./coffee_plus.md) .

## Internationalisering af hjemmesider og dokumenter

Byg videre på følgende 3 projekter

### [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

Markdown-skabelonen med suffikset `.mdt` , kan henvise til eksterne filer med en syntaks svarende til `<+ ./coffee_plus/import.js>` .

[@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

Markdown-oversættelse vil ikke oversætte koder og links og vil cache oversatte sætninger. Hvis oversættelsen er ændret, men den originale tekst ikke er ændret, vil det ikke overskrive ændringen af ​​oversættelsen, hvis du udfører den igen.

[@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

Sprogfiler til oversættelse `yaml` genererede websteder.
