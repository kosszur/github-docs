---
title: About contributing to GitHub Docs
shortTitle: About contributing
intro: 'A GitHub-dokumentumok tartalmához többféle módon is hozzájárulhat.'
versions:
  feature: 'contributing'
---

A {% data variables.product.prodname_dotcom %} dokumentációja nyílt forráskódú. Bárki hozzájárulhat (contribute) a dokumentumokhoz a nyilvános `docs` repository-ban: https://github.com/github/docs. A {% data variables.product.prodname_dotcom %} alkalmazottai ennek repository-nak a `docs-internal` nevű  másolatában dolgoznak a dokumentáción. A két repository automatikusan szinkronizálja a rendszer, hogy mindkettő naprakész legyen az bármelyik repository `main` branch-ében merge-elt változtatásokkal. (The two repositories are automatically synced to keep them both up to date with changes merged into the `main` branch of either repository.) Az egyszerűség kedvéért a {% data variables.product.prodname_docs %}-hoz való hozzájárulásról szóló cikkekben a "a dokumentációs repository"-ra / "the documentation repository" hivatkozunk.

A dokumentációs repository az itt [docs.github.com](/) közzétett dokumentáció megvitatásának és együttműködésének helye. (The documentation repository is the place to discuss and collaborate on the documentation that is published here on [docs.github.com](/).<!-- markdownlint-disable-line search-replace -->)

## Issues

A problémák ([Issues](/github/managing-your-work-on-github/about-issues)) nyomon követésére szolgálnak azok a feladatok, amelyekben a közreműködők (contributors) segíthetnek. Ha egy problémának (issue) van `triage` (osztályozási) címkéje, még nem vizsgáltuk át (reviewed), és ne kezdjen vele foglalkozni.

Ha talált valamit a dokumentációban vagy a docs.github.com webhelyen, amit frissíteni kell, keressen a nyitott problémák között, hátha valaki más is jelentett-e ugyanezt. Ha valami új, nyisson meg egy problémát egy [sablon (template)](https://github.com/github/docs/issues/new/choose) segítségével. A problémát (issue) arra használjuk, hogy megbeszéljük a megoldani kívánt problémát (problem). (We'll use the issue to have a conversation about the problem you'd like to be fixed.) <!-- markdownlint-disable-line search-replace -->

{% note %}

**Note**: A {% data variables.product.prodname_dotcom %} alkalmazottainak a privát  `docs-content` repository-ban kell megnyitniuk a problémákat (issues).

{% endnote %}

## Pull requests

Egy [pull request](/github/collaborating-with-issues-and-pull-requests/about-pull-requests) egy módja annak, hogy változtatásokat javasoljunk a repository-nkban. Amikor ezeket a változtatásokat merge-ljük (egyesítjük), 24 órán belül deploy-oljuk (üzembe helyezzük) őket az élő webhelyen.

Hozzájárulást nem tudunk elfogadni [REST API reference documentation](/rest/reference). Ha pontatlanságot észlel a REST API referencia-dokumentációjában, nyiss egy issue-t a [`rest-api-description`](https://github.com/github/rest-api-description/issues/new?template=schema-inaccuracy.md) repository-ban.

Csak a {% data variables.product.prodname_dotcom %} -termékeket, -szolgáltatásokat (features), -eszközöket (tools) és -bővítményeket (extensions) dokumentáljuk. Megemlíthetünk third-party tools (harmadik féltől származó eszközöket) vagy hivatkozhatunk rájuk annak bemutatására, hogyan működik egy funkció, de nem fogadunk el pull request-eket a third-party tools (harmadik féltől származó eszközök) vagy integrációk dokumentálására, kivéve, ha azokat a {% data variables.product.company_short %} segítségével fejlesztették ki.(unless they were codeveloped with {% data variables.product.company_short %}.)

### Reviewing your own pull requests

Mindig először a saját pull request-ét tekintse át (review), mielőtt megjelölné mások általi felülvizsgálatra (review-ot) készként. (You should always review your own pull request first, before marking it as ready for review by others.)

Tartalmi módosítások esetén győződjön meg róla (For content changes, make sure that you) :

* Győződjön (Confirm) meg arról, hogy a változtatások megfelelnek a felhasználói élménynek és a tartalomtervezési tervben (ha van ilyen) megfogalmazott céloknak.
* Tekintse át (Review) a tartalmat a műszaki pontosság (technical accuracy) érdekében.
* Ellenőrizze (Check) a módosítások nyelvtani, helyesírási és a [AUTOTITLE](/contributing/style-guide-and-content-model/style-guide) betartását (adherence).
* Győződjön (Make sure) meg arról, hogy a pull request szövege könnyen lefordítható. További információért, lásd:  "[AUTOTITLE](/contributing/writing-for-github-docs/writing-content-to-be-translated)."
* Ellenőrizze az új vagy frissített Liquid utasításokat (Liquid statements), hogy megbizonyosodjon (confirm) arról, hogy a verziószám helyes. További információért, lásd:  "[AUTOTITLE](/contributing/syntax-and-versioning-for-github-docs/versioning-documentation)."
* Ellenőrizze a módosított oldalak előnézetét. A pull request elküldése után automatikusan létrejön egy előnézet, és a linkek hozzáadásra kerülnek a pull request-hez. Az előnézet néha több percig is eltart, mire készen áll a megtekintésre. Győződjön (Confirm) meg arról, hogy minden a várt módon történik. Az előnézet ellenőrzése segít azonosítani a problémákat, például az elírási hibákat, a stílus útmutatót nem követő tartalmat, vagy a verziókezelési problémák miatt nem renderelő tartalmat (content that isn't rendering due to versioning problems). Ügyeljen arra (Make sure to), hogy a megjelenített (rendered) kimenetben ellenőrizze a listákat és a táblázatokat, amelyek néha olyan problémákat okozhatnak, amelyeket nehéz azonosítani a Markdownban.
* Ha a pull request-edben hibás ellenőrzések szerepelnek, végezze el a hibaelhárítást (troubleshoot) mindaddig, amíg mindegyik sikeres lesz.

## Support

We are a small team working hard to keep up with the documentation demands of a continuously changing product. Unfortunately, we just can't help with support questions in this repository. If you are experiencing a problem with {% data variables.product.prodname_dotcom %}, unrelated to our documentation, please [contact {% data variables.product.prodname_dotcom %} Support directly](https://support.github.com/contact). Any issues or pull requests opened in the documentation repository requesting support will be given information about how to contact {% data variables.product.prodname_dotcom %} Support, then closed and locked.

If you're having trouble with your {% data variables.product.prodname_dotcom %} account, contact [Support](https://support.github.com/contact?tags=docs-contributing-guide).

## Translations

Ez a weboldal nemzetközi és több nyelven is elérhető. A repository forrástartalma angol nyelven íródott. A fordításokat belső folyamaton keresztül automatizáljuk, professzionális fordítókkal együttműködve az angol tartalom lokalizálása érdekében.

Ha fordítási hibát észlel, kérjük, jelezze a problémát (issue) a részletekkel.

Jelenleg nem fogadunk el lefordított tartalomra vonatkozó pull requests-et.

## Site policy

{% data variables.product.prodname_dotcom %}'s site policies are also published on docs.github.com.<!-- markdownlint-disable-line search-replace -->

If you find a typo in the site policy section, you can open a pull request to fix it. For anything else, see "[Contributing](https://github.com/github/site-policy/blob/main/CONTRIBUTING.md)" in the `site-policy` repository.
