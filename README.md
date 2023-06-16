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

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Suffikset er `.mdt` , du kan bruge syntaksen svarende til `<+ ./coffee_plus/import.js>` til at henvise til eksterne filer og generere markdown med suffikset `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Markdown-oversættelse vil ikke oversætte koder og links og vil cache oversatte sætninger. Hvis oversættelsen er ændret, men den originale tekst ikke er ændret, vil det ikke overskrive ændringen af ​​oversættelsen, hvis du udfører den igen.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Sprogfiler til oversættelse `yaml` genererede websteder.

### Dokumentoversættelsesautomatiseringsinstruktioner

Se repository [xxai-art/doc](https://github.com/xxai-art/doc)

Det anbefales at installere nodejs, [direnv](https://direnv.net) og [bun](https://github.com/oven-sh/bun) først, og derefter køre `direnv allow` efter indtastning af mappen.

For at undgå alt for store lagre oversat til hundredvis af sprog, oprettede jeg et separat kodelager for hvert sprog og oprettede en organisation til at opbevare dette lager.

Indstilling af miljøvariablen `GITHUB_ACCESS_TOKEN` og derefter kørsel af [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) vil automatisk oprette lageret.

Du kan selvfølgelig også stille den på et lager.

Oversættelsesscriptreference [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Scriptkoden fortolkes som følger:

[bunx](https://bun.sh/docs/cli/bunx) er en erstatning for npx, som er hurtigere. Hvis du ikke har bun installeret, kan du selvfølgelig bruge `npx` i stedet for.

`bunx mdt zh` gengiver `.mdt` i zh-mappen som `.md` , se de 2 linkede filer nedenfor

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` er kernekoden til oversættelse (hvis du kun har `nodejs` installeret, men `bun` og `direnv` ikke er installeret, kan du også køre `npx i18n` for at oversætte).

Den vil parse [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , konfigurationen af `i18n.yml` i dette dokument er som følger:

```
en:
zh: ja ko en
```

Betydningen er: kinesisk oversættelse til japansk, koreansk, engelsk, engelsk oversættelse til alle andre sprog. Hvis du kun vil støtte kinesisk og engelsk, kan du bare skrive `zh: en` .

Den sidste er [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , som udtrækker indholdet mellem hovedtitlen og den første undertitel af hvert sprogs `README.md` for at generere en indgang `README.md` . Koden er meget enkel, du kan selv se på den.

Google API bruges til gratis oversættelse. Hvis du ikke kan få adgang til Google, skal du konfigurere og indstille en proxy, såsom:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Oversættelsesscriptet vil generere en oversættelsescache i `.i18n` biblioteket, tjek det med `git status` og føj det til kodelageret for at undgå gentagne oversættelser.
