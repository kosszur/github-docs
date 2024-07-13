---
title: Using the TODOCS placeholder to leave notes
shortTitle: Using the TODOCS placeholder
intro: 'A TODOCS placeholder-el jelezheti a még befejezésre váró munkákat.'
versions:
  feature: 'contributing'
---

<!-- markdownlint-disable search-replace -->
## Using the TODOCS placeholder

A műszaki írók néha helyőrzőket (placeholder) használnak a dokumentáció írása közben, hogy emlékeztessenek arra, hogy valamire később térjenek vissza. Hasznos technika, de mindig fennáll annak a lehetősége, hogy a helyőrzőt figyelmen kívül hagyják, és becsúsznak az éles környezetbe (slip into production). Ezen a ponton, a Docs csapata csak úgy értesülhet róla, ha valaki meglátja és bejelenti.

A csúszások elkerülése érdekében (To prevent slips) használja a `TODOCS` karakterláncot helyőrzőként. A Docs tesztcsomagja (test suite) tartalmaz egy [linting test](https://github.com/github/docs/tree/main/src/content-linter), amely sikertelen lesz, ha bárhol megtalálja ezt a karakterláncot egy Markdown vagy YAML fájlban.

{% note %}

**Note**:
Ha a {% data variables.product.prodname_vscode_shortname %}-ot használja szövegszerkesztőként, a "[TODO Highlight](https://marketplace.visualstudio.com/items?itemName=wayou.vscode-todo-highlight)" kiterjesztés hasznos a "TODOCS" példányainak kiemeléséhez a fájlokban. Adja hozzá a "TODOCS"-t és a kis- és nagybetűk más változatait, például a "todocs,"-t a bővítmény beállításaihoz.

{% endnote %}

### Example

```markdown
1. In the dropdown, select the settings you want to sync.

   TODOCS: ADD A SCREENSHOT OF THE SETTINGS SYNC OPTIONS

1. Click **Sign in & Turn on**, then select the account to which you want your settings to be synced.
```
<!-- markdownlint-enable search-replace -->
