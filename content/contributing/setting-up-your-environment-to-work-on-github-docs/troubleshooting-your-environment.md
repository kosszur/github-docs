---
title: Troubleshooting your environment
intro: "Tudjon meg többet a helyi környezetben és a {% data variables.product.prodname_docs %} staging platformján felmerülő problémák hibaelhárításáról."
versions:
  feature: 'contributing'
---

## Troubleshooting tests that fail locally but pass in CI

Ha helyben futtatja a teszteket, és hibákat kap a `tests/rendering/server.js` a statikus eszközök (assets), stíluslapok vagy az ügyféloldali JavaScript-bundle (köteg) körül, de ugyanezek a tesztek a CI-ben is megfelelnek egy PR-on, futtassa a  `npm run build` parancsot. Ez egy egyszeri parancs, amely statikus eszközöket (assets) hoz létre helyben.

További információért, lásd:  "[AUTOTITLE](/contributing/setting-up-your-environment-to-work-on-github-docs/creating-a-local-environment)."

## Troubleshooting stalled staging deployments

Ha több mint tíz percig függőben van egy staging deployment, próbálja meg bezárni a pull request (a branch törlése nélkül), majd nyissa meg újra. Ez új staging deployment-et indít el. Nem fog eltörni semmit.

Ha ez nem működik, használja az alábbi parancsokat, hogy elindítson egy új staging deployment-et úgy, hogy egy üres commit-ot push-ol a parancssorban.( use the commands below to trigger a new staging deployment by pushing an empty commit on the command line.)

```shell
git commit --allow-empty -m 'empty commit to redeploy staging'
git push
```

## Troubleshooting stalled or stuck  CI

Ha a tesztek több mint egy órán keresztül "In progress" vagy "Pending" állapotban vannak, az alábbi parancsokkal futtassa újra a CI-t úgy, hogy egy üres commit-ot push-ol a parancssorban (to rerun CI by pushing an empty commit on the command line.)

```shell
git commit --allow-empty -m 'empty commit to rerun CI'
git push
```

## Troubleshooting local server problems

Ha az `npm start` parancsot futtatja, és a `Cannot find module` hibaüzenetet kapja, próbálja ki a következő parancsot a server újraindítása előtt.

```shell
npm install
```

Ha ez nem oldja meg a problémát, használja a következő parancsot a `node_modules` könyvtár eltávolításához és újratelepítéséhez.

```shell
rm -rf node_modules
npm install
```

## Troubleshooting staging problems

Ha problémái vannak az staging server-el, akkor a hibával kapcsolatos további információknak kell megjelenniük a böngészőben vagy a parancssorban, ha helyben futtatja a webhelyet. Nézze meg local branch-ét, és használja a következő parancsot a helyi szerver elindításához.

```shell
npm start
```

Amikor a szerver fut, keresse meg a problémás cikket a `https://localhost:4000` címen a böngészőjében. Az staging server csak "Oops" hibát jelenít meg, de a helyi szervernek stack trace-t kell mutatnia a hibakereséshez (debugging).

Ha az alábbihoz hasonló hibát lát, győződjön meg arról, hogy az idézőjelek (single quotes) megfelelően vannak kiírva a formázóban. Ezenkívül ellenőrizze a `redirect_from` blokkok formázását is. További információért, lásd:  "[AUTOTITLE](/contributing/syntax-and-versioning-for-github-docs/using-yaml-frontmatter#escaping-single-quotes)."

```text
error parsing file: /Users/z/git/github/docs/content/dotcom/articles/troubleshooting-custom-domains-and-github-pages.md
(node:89324) UnhandledPromiseRejectionWarning: YAMLException: can not read a block mapping entry; a multiline key may not be an implicit key at line 4, column 14:
    redirect_from:
                 ^
```

## Checking internal links

The "Link Checker: On PR" test reports broken links on the site, including images. If there are broken links, the test will fail and the test's details view will show either `TitleFromAutotitleError` errors, which just report the broken link URL, or a more descriptive report which also lists the page that contains the broken link.

If the error does not include the location of the broken link, you will need to search the `docs` repository for the broken link to find the file.

When you locate the broken link, make sure the link is versioned correctly. For example, if the article only exists for GHES version 3.8+, make sure the link is versioned for 3.8+.

If an article that is available for {% data variables.product.prodname_ghe_server %} links to a {% data variables.product.prodname_dotcom_the_website %}-only article, include the version in the path to prevent the URL from automatically converting to include a {% data variables.product.prodname_ghe_server %} version number. The following example demonstrates how to link from a {% data variables.product.prodname_ghe_server %} article to a {% data variables.product.prodname_dotcom_the_website %}-only article.
  
```text
[{% raw %}{{ data variables.product.prodname_github_connect }} Addendum to the {{ data variables.product.prodname_enterprise }} License Agreement{% endraw %}](/free-pro-team@latest/articles/github-connect-addendum-to-the-github-enterprise-license-agreement/)"
```

## Debugging locally

A fejlesztés során felkeresheti a `http://localhost:4000` bármely oldalát, és hozzáadhatja a `?json=page` karakterláncot az elérési út végéhez, hogy megmutasson néhány mögöttes információt, amely hasznos lehet a hibakereséshez. Az olyan alapvető információkon kívül, mint a cím és a bevezető, ezek a mezők hasznosak lehetnek.

| Mező | Description |
| ----- | ----------- |
|`productVersions` | Shows what the site is parsing from the `productVersions` frontmatter.
| `permalinks` | Megjeleníti az összes állandó hivatkozást (permalinks), amelyet a webhely az oldalhoz generál.
| `redirect_from` | Shows the hardcoded redirects in the `redirect_from` frontmatter.
| `redirects` | Megjeleníti az összes átirányítást, amelyet a webhely az oldalhoz generál.
| `includesPlatformSpecificContent` | Megmutatja, hogy a webhely észlel-e platformspecifikus tartalmat az oldalon.

## Working with liquid processing

Ha a szöveg vagy példakódja zárójelek (`{` és `}`) között tartalmaz tartalmat, akkor a <code>&#123% raw %&#125;</code> és a <code>&#123% raw %&#125;</code> címkék közé kell csomagolnia az adott szakasz Liquid processing (folyékony feldolgozásának) letiltásához. (to disable Liquid processing for that section.) Például:

* **Use**:

  <pre>
  GITHUB_TOKEN: &#123% raw %&#125;${% raw %}{{ secrets.GITHUB_TOKEN }}{% endraw %}&#123% endraw %&#125;
  </pre>

* **Avoid**:

  <pre>
  GITHUB_TOKEN: ${% raw %}${{ secrets.GITHUB_TOKEN }}${% endraw %}
  </pre>
