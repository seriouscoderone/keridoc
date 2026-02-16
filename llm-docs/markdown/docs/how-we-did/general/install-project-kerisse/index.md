# Install this repo

Result: | @kordwarshuis TBW |

What is this: [Github README](https://github.com/weboftrustkeridoc/README) describes the download, install, configuration and launch of this project.

For who: site maintainer

-   Clone this repository
-   Run `npm install`
-   Install four extra libraries manually (for the scrapers functionality):
    -   `jq` ([https://stedolan.github.io/jq/](https://stedolan.github.io/jq/))
    -   `curl` ([https://curl.se/](https://curl.se/))
    -   `ImageMagick` ([https://imagemagick.org](https://imagemagick.org))
    -   `sitemap-generator-cli` ([https://github.com/lgraubner/sitemap-generator-cli](https://github.com/lgraubner/sitemap-generator-cli))

To install `jq`, `curl`, `ImageMagick`, use a package manager e.g., apt, yum, brew, etc.

To install `sitemap-generator-cli` look here: [https://github.com/lgraubner/sitemap-generator-cli?tab=readme-ov-file#install](https://github.com/lgraubner/sitemap-generator-cli?tab=readme-ov-file#install)

Now you can refresh the **search index** if needed: `$ sh search-index-typesense/main.sh`

This takes about half an hour.

Instructions on how to use createSitemap.js: [https://github.com/WebOfTrustkeridoc/blob/main/search-index-typesense/createSitemap.mjs](https://github.com/WebOfTrustkeridoc/blob/main/search-index-typesense/createSitemap.mjs)