# Github Actions

This article is for maintainers, but also users who'd like to know what actions get triggered by what type of events.

Results: insight in the choice around our Coninuous Development Continuous Integration (CDCI) process.

Github Actions are readible for most people who are able to read pseudo-code. The structure and organization of our Action scripts and those brought in by third party tools like Docusaurus, can be distilled fom the [source code](https://github.com/WebOfTrustkeridoc/tree/main/.github/workflows). However, we 'd like to offer a convenient insight in the structure and working.

-   script are set off by hand or automatic? Or both? In which situation would you apply these options.
-   are certain Action scripts calling eachtother? If so it needs to be clear under what circumstances.

There are currently five Github Actions. All actions should be started manually. One script is started via Cron: the “Find broken links” action. No actions are triggered by Push commits.

This means that after updating the Wiki, you should run the “Import wiki” action manually to get the new content into this repo. If you wish to publish the new content to the website, you should run “Deploy to Github Pages”.

The same goes for importing external glossaries and importing metadata.

1.  **[Deploy to Github Pages](https://github.com/WebOfTrustkeridoc/actions/workflows/deploy-to-gh-pages.yml)**:
    -   runs on workflow\_dispatch (manual start)
    -   receives changes that are pushed (content updates, e.g. HowTo's, or design updates)
    -   builds and copies _/build_ to gh-pages
2.  **[Find broken links](https://github.com/WebOfTrustkeridoc/actions/workflows/find-broken-links.yml)**:
    -   runs on _cron_ and _workflow\_dispatch_ (manual start)
    -   checks links
    -   creates issue
3.  **[Import external glossaries](https://github.com/WebOfTrustkeridoc/actions/workflows/import-external-glossaries.yml)**:
    -   runs on _workflow\_dispatch_ (manual start)
    -   updates external glossaries
    -   pushes updates into repo
4.  **[Import meta data from google sheets](https://github.com/WebOfTrustkeridoc/actions/workflows/import-metadata-google-sheet.yml)**:
    -   runs on _workflow\_dispatch_ (manual start)
    -   updates meta data from google sheet
    -   pushes updates into repo
5.  **[Import wiki](https://github.com/WebOfTrustkeridoc/actions/workflows/import-wiki.yml)**:
    -   runs on workflow\_dispatch (manual start)
    -   copies wiki to /docs/glossary
    -   pushes changes into repo
6.  **Scraper**: To Be Created
    -   runs on _workflow\_dispatch_:
    -   scrapes various sources
    -   imports result into Typesense, makes backup, etc
    -   pushes updates into repo