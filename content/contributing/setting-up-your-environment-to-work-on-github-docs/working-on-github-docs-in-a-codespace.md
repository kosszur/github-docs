---
title: Working on GitHub Docs in a codespace
shortTitle: Working in a codespace
intro: 'A {% data variables.product.prodname_github_codespaces %} segítségével dolgozhat a {% data variables.product.prodname_docs %} dokumentációján.'
versions:
  feature: 'contributing'
---

## About {% data variables.product.prodname_github_codespaces %}

{% data variables.product.prodname_github_codespaces %} lehetővé teszi, hogy olyan fejlesztői környezetben dolgozzon, amelyet távolról üzemeltetnek a számítógépéről. Gyorsan elkezdheti, anélkül, hogy be kellene állítania a munkakörnyezetet vagy le kellene töltenie fájlokat a helyi számítógépére.

További információért olvassa el a "[AUTOTITLE](/free-pro-team@latest/codespaces/overview)." című részt.

## Working on documentation in a codespace

A következő lépések feltételezik, hogy a  {% data variables.product.prodname_github_codespaces %} be van állítva a fájlok szerkesztéséhez a {% data variables.product.prodname_vscode %} for Web használatával. A lépések nagyon hasonlóak, ha másik szerkesztőt állított be. További információkért lásd "[AUTOTITLE](/free-pro-team@latest/codespaces/customizing-your-codespace/setting-your-default-editor-for-codespaces)."

1. Keresse meg a nyílt forráskódú {% data variables.product.prodname_docs %} repository-t,  [`github/docs`](https://github.com/github/docs).
1. If you're an open source contributor, hozz létre a repository-nak egy fork-ját, majd kövesd ennek az eljárásnak a többi lépését a fork-odból. További információkért lásd "[AUTOTITLE](/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)."
1. Create a branch to work on. További információkért lásd "[AUTOTITLE](/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository)."
1. On the main page of the repository, click **{% octicon "code" aria-hidden="true" %} Code**, then click **Create codespace on BRANCH-NAME**.

   Megjelenik a "Setting up your codespace" /„Kódtér beállítása” oldal. Rövid idő múlva megjelenik a {% data variables.product.prodname_vscode %} böngésző alapú verziója.
1. Use the Explorer to navigate to the markdown file you want to edit. If the file is an article, it will be located in the `content` directory. If the file is reusable content, it will be located in the `data` directory.

   In most cases, the path to an article in the `content` directory matches the path in the URL, minus the `.md` file extension. For example, the source for the article `https://docs.github.com/en/codespaces/getting-started/quickstart` is the markdown file `content/codespaces/getting-started/quickstart.md`.<!-- markdownlint-disable-line search-replace -->
1. Szükség szerint szerkessze a markdown fájlt.
1. Mentse el a változtatásokat.
1. Commit and push your changes, either using the Source Control view, or using Git commands from the Terminal. További információkért lásd "[AUTOTITLE](/get-started/using-git/about-git)."

## Creating a pull request

1. Navigate to the "Pull requests" tab of the `github/docs` repository at [github.com/github/docs/pulls](https://github.com/github/docs/pulls).
1. Click **New pull request**.
1. If you're an open source contributor, click **compare across forks**, then choose the forked repository you created and your working branch.

   Otherwise, change the "compare" branch to your working branch.
1. Check that the changes displayed include all of the changes you made in the codespace. If they do not, this may indicate there are changes you have not pushed from the codespace to {% data variables.product.prodname_dotcom %}.
1. Click **Create pull request**.
1. Enter the details for your pull request and click **Create pull request**.

   Your pull request will be reviewed by a member of the {% data variables.product.prodname_docs %} team.
