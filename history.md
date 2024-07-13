



## 2024-07-13

### forkolás és branch létrehozása

- docs alapján [leírtak](https://docs.github.com/en/contributing/setting-up-your-environment-to-work-on-github-docs/working-on-github-docs-in-a-codespace) alapján forkoltam és létrehoztam egy `hu` branchet

## helyi környezet 

- docs alapján [leírtak](https://docs.github.com/en/contributing/setting-up-your-environment-to-work-on-github-docs/creating-a-local-environment) alapján klónoztam
- új branchre chechoutoltam 
- fordítottam

elméletileg csak ennyi:

```
git clone https://github.com/github/docs
cd docs
npm ci
npm start
```

### problémák és megoldások

- régi volt az `npm` a gépen így azt is frissíteni kellett újabbra

- Windowson kaptam a `npm ci`-re, hogy `'cp' is not recognized as an internal or external command` szóval
  - a `package.json`-be kellett átírni a `cp` parancsot `copy`-ra ([ihhlet más problémáiból](https://github.com/mschwarzmueller/reactjs-basics/issues/2) )

- utána viszont már a `ci` hozzáadta a szükséges `node_modules` elemeket és a start elindította a `4000`-es porton a szervert







