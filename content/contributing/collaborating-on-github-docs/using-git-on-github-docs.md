---
title: Using Git on GitHub Docs
shortTitle: Using Git
intro: 'A parancssorban a Git segítségével commit-olhatja (véglegesítheti) a változtatásokat, majd push-ohatja (elküldheti) azokat a dokumentációs repository-ba.'
versions:
  feature: 'contributing'
---

Ez a cikk a dokumentációs repository topic branch-ének létrehozását, a változtatások commitolásának (véglegesítésének) és a módosítások távoli repository-ba való push-olásának (visszaküldésének) folyamatát írja le.

A cikk feltételezi, hogy már klónozta a dokumentációs repository-t helybe, és a módosításokat a helyi számítógépen hajtja végre, nem pedig a {% data variables.product.prodname_dotcom_the_website %} webhelyen vagy egy codespace-ben (kódtérben). További információért, lásd:  "[AUTOTITLE](/repositories/creating-and-managing-repositories/cloning-a-repository?tool=webui)."

## Setting up your topic branch and making changes

Tartsd szinkronba a helyi branch-edet a távolival és kerüld el a merge conflict-okat, kövesse az alábbi lépéseket a dokumentáción való munka során.

1. A terminálban módosítsa az aktuális munkakönyvtárat arra a helyre, ahol a dokumentációs repository klónozta. Például:

   ```shell
   cd ~/my-cloned-repos/docs
   ```

1. Váltson az alapértelmezett branch-re: `main`.

   ```shell
   git checkout main
   ```

1. Húzd le a legutóbbi commitokat a remote repository-ból.

   ```shell
   git pull origin main
   ```

1. Váltson át (Switch to) vagy hozzon létre egy topic branch-et (témaágat).
   * Új projekt indításához hozzon létre egy új topic branch-et (témaágat) a `main`-ből.

     ```shell
     git checkout -b YOUR-TOPIC-BRANCH
     ```

     {% note %}

     **Note**: Használhat perjelet (forward slashes) a branch-név részeként, például a felhasználónév megadásához:

     ```shell
     git checkout -b my-username/new-codespace-policy
     ```

     {% endnote %}

   * Ha egy meglévő projekten szeretne dolgozni, váltson át a topic branch-ére, és merge-elja (egyesítse) a módosításokat `main`-ből. (switch to your topic branch and merge changes from `main`.)

     ```shell
     git checkout YOUR-TOPIC-BRANCH
     git merge main
     ```

     Ha merge conflict-sba (összevonási ütközésekbe) futott bele, kövesse a jelen cikk későbbi lépéseit az [resolving merge conflicts (összevonási ütközések feloldásához)](#resolving-merge-conflicts).

1. Nyissa meg a kívánt szövegszerkesztőt, szerkessze a fájlokat szükség szerint, majd mentse a módosításokat.

## Committing and pushing your changes

1. Ha készen állnak a változtatások a commit-ra (véglegesítésére), nyisson meg egy terminált, és ellenőrizze a topic branch (témaág) állapotát a `git status`-tal. Győződjön meg arról, hogy a megfelelő módosításkészletet (set of changes) látja.

   ```shell
   git status
   On branch YOUR-TOPIC-BRANCH

   Changes not staged for commit:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
           deleted:    example-deleted-file.md
           modified:   example-changed-file.md

   Untracked files:
     (use "git add <file>..." to include in what will be committed)
           example-new-file.md
   ```

1. Stage-elje (Állítsa össze) a módosított fájlokat úgy, hogy készen álljanak a topic branch (témaágban) való commitolásra (véglegesítés).

   * Ha új fájlokat hozott létre vagy frissítette a meglévő fájlokat, használja a `git add FILENAME [FILENAME...]` parancsot. Például:

     ```shell
     git add example-new-file.md example-changed-file.md
     ```

     Ez hozzáadja a fájlok frissített verzióját a Git staging area-jához (összeállítási területéhez), ahonnan a változtatások commitolhatók (véglegesíthetők). Egy fájl unstage-éhez (összeállított állapotának megszüntetéséhez) használja a `git reset HEAD FILENAME`. Például, `git reset HEAD example-changed-file.md`.

   * Ha törölted a fájlokat, használd a `git rm FILENAME [FILENAME...]` parancsot. Például:

     ```shell
     git rm example-deleted-file.md
     ```

1. Commit-olja (véglegesítse) a változtatásait (Commit your changes).

   ```shell
   git commit -m "Commit message title (max 72 characters)
   
   Optional fuller description of what changed (no character limit). 
   Note the empty line between the title and the description, 
   and the closing quotation mark at the end of the commit message."
   ```

   Ez commit-olja (véglegesíti) az helyileg összeállított változásokat. (This commits the staged changes locally.) Ezt a commit-ot és minden más nem push-olt commit-ot most a remote (távoli) repository-ba küldheti. (You can now push this commit, and any other unpushed commits, to the remote repository.)  

   A commit (véglegesítés) eltávolításához használja a `git reset --soft HEAD~1`. Ennek a parancsnak a futtatása után a változtatásaink már nem commitáltak (végletgesítettek), de a módosított fájlok az összeállítási területen (staging area) maradnak. (After running this command our changes are no longer committed but the changed files remain in the staging area.) További módosításokat végezhet (You can make further changes), majd `add` és `commit` ismét.

1. Push-old (told fel) a módosításaidat a remote (távoli) repository-ba a {% data variables.product.prodname_dotcom_the_website %}-on.

   * Amikor először push-olod (tolod) a branch-et, hozzáadhat egy upstream tracking branch-et. Ez lehetővé teszi a `git pull` és a `git push` használatát ezen az branch-en további argumentumok nélkül.

     ```shell
     git push --set-upstream origin YOUR-TOPIC-BRANCH
     ```

   * Ha korábban már push-olta (toltad) ezt a branch-et, és beállított egy upstream tracking branch-et, használd:

     ```shell
     git push
     ```

### Best practices for commits

* Előnyben részesítse azokat a commit-okat (véglegesítéseket), amelyek kis, fókuszált változtatási csoportokat tartalmaznak, mint a nagy, nem fókuszált változtatási csoportokat tartalmazó commitokat (véglegesítéseket), mivel ez segít olyan commit message (üzenetek) megírásában, amelyeket mások könnyen megértenek. Kivételt képez egy új projekt vagy kategória initial commit-ja (kezdeti véglegesítése). Ezek a commit-ok néha nagyok, mivel gyakran több cikk puszta változatát vezetik be egyszerre, hogy szervezeti sémát adjanak a későbbi munkához. (These commits are sometimes large, as they often introduce the bare versions of many articles at once to provide an organizational scheme for subsequent work.)
* Ha feedback-et (visszajelzést) szeretne beépíteni (incorporating), vagy egy adott személy vagy csapat változásait szeretné review-zni (értékelni), @mention -ölje (említse meg) azt a személyt, akinek javaslatait beépíti (whose suggestions you are incorporating). Például: "Incorporating feedback from @octocat," vagy "Updating billing configuration steps - cc @monalisa for accuracy.".
* Ha egy commit (véglegesítés) megold egy issue-t (If a commit addresses an issue), hivatkozhat a issue számra a commit-ban, és a commit-ra mutató hivatkozás jelenik meg az issue conversation (megbeszélés) idővonalán: "Addresses #1234 - adds steps for backing up the VM before upgrading."
  {% note %}

  **Note**: Általában nem zárunk le egy issue-t (ügyet) egy commit-tal. Egy issue (probléma) lezárásához nyisson meg egy pull request-et, és adja hozzá a "Closes #1234" kifejezést a leíráshoz. A linked issue (kapcsolt probléma) a pull request merge-elésekor (egyesítésekor) lezárul. További információért, lásd:  "[AUTOTITLE](/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue)."

  {% endnote %}
* Legyenek a commit message-ek egyértelműek, részletesek és szükségszerűek (clear, detailed, and imperative). Például: "Adds a conceptual article about 2FA," és nem "Add info."
* Lehetőleg ne hagyjon uncommitted (véglegesítetlen) változtatásokat a local branch-eden, amikor befejezi a napi munkát. Kerüljön el egy jó megállóhelyre, és commit-old, és push-old a változtatásokat, hogy a munkájáról biztonsági másolat készüljön a remote (távoli) repository-ba.
* Csak néhány commit után push-old fel a {% data variables.product.prodname_dotcom_the_website %} oldalra. Ha minden commit után push-olunk, az megnöveli a műveleti csatornáinkat zajosságát a Slack-en, és szükségtelen buildeket eredményez.

## Resolving merge conflicts

Ha két olyan branch-et próbál merge-elni (egyesíteni), amelyek egy fájl ugyanazon részének különböző módosításait tartalmazzák, merge conflict-ot (összevonási ütközést) fog kapni. Munkafolyamatunkban ez leggyakrabban akkor fordul elő, amikor a `main`-t egy local topic branch (helyi témaágba) merge-eljük (egyesítjük).

A merge conflict-ok (összevonási ütközések) kezelésének két módja van:
* Szerkessze a fájlt a szövegszerkesztőben, és válassza ki, mely változtatásokat szeretné megtartani. Ezután commit-olja (véglegesítse) a frissített fájlt a topic branch-eden (témaágben) a parancssorból.
* [Oldja meg (Resolve) a merge conflict-okat {% data variables.product.prodname_dotcom_the_website %}-on](/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-on-github).

### Resolving merge conflicts by editing the file and committing the changes

1. A parancssorban jegyezze fel az merge conflict-okat tartalmazó fájlokat. (On the command line, note the files that contains merge conflicts.
1. Nyissa meg az első fájlt a szövegszerkesztőben.
1. Keresse meg a fájlban az merge conflict jelzőket.

   ```text
    <<<<<<< HEAD
    Here are the changes you've made.
    =====================
    Here are the changes from the main branch.
    >>>>>>> main
   ```

1. Döntse el, mely változtatásokat kívánja megtartani, és törölje a nem kívánt változtatásokat és a merge conflict jelzőket. Ha további változtatásokat kell végrehajtania, azt egyidejűleg megteheti. Például megváltoztathatja az előző kódmintában látható öt sort egyetlen sorra:

   ```text
   Here are the changes you want to use.
   ```

   Ha több fájl is merge conflict-os, ismételje meg az előző lépéseket, amíg az összes ütközést meg nem oldja (resolve all conflicts).

   {% note %}

   **Note**: Óvatosan kell eljárnia az merge conflict feloldásakor. (You should apply care when resolving merge conflicts.) Néha egyszerűen elfogadja a saját módosításait, néha a `main` branch-ból az upstream módosításait fogja használni (sometimes you will use the upstream changes from the `main` branch), néha pedig kombinálja a két változáskészletet. Ha nem biztos a legjobb felbontásban, ügyeljen arra, hogy a upstream-ból jövő módosításokat cserélje ki, mivel ezek olyan konkrét okok miatt történhettek, amelyekről nem tud. (If you're unsure of the best resolution, be wary of replacing the changes from upstream as these may have been made for specific reasons that you're not aware of.)

   {% endnote %}

1. A terminálban állítsa össze (stage) az imént módosított fájlt vagy fájlokat.

   ```shell
   git add changed-file-1.md changed-file-2.md
   ```

1. Commit-álja a fájlokat.

   ```shell
   git commit -m "Resolves merge conflicts"
   ```

1. Push-olja (Tolja be) a commit-ált (végrehajtott) módosításokat a remote (távoli) repository-ba a {% data variables.product.prodname_dotcom_the_website %} webhelyen.

   ```shell
   git push
   ```

## Creating a pull request

Javasoljuk, hogy mielőbb nyissa meg pull request-et a {% data variables.product.prodname_dotcom %}-on. Hozza létre vázlatként a pull request-et, amíg nem áll készen a review-ra (ellenőrzésre). Minden alkalommal, amikor push-olja (leküldi) a változtatásokat, a commit-jaid hozzáadódik a pull request-hez.

{% note %}

**Note**: Gyorsan elérheti az Ön által létrehozott pull request-eket, ha a {% data variables.product.prodname_dotcom_the_website %} minden oldalának tetején lévő **Pull requests** elemre kattint.

{% endnote %}

További információért, lásd: "[AUTOTITLE](/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request?tool=webui#creating-the-pull-request)."
