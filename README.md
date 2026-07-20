# LongFi Website Work

Source files, page snippets, and assets for building and updating longfisolutions.com.

## snippets/

Current WordPress / Elementor Woody snippet files, one per page (`lf-<page>.html`), each scoped to `#lf-<page>`. These are the source of truth for the live Woody snippets. Files are served as raw URLs so the update tooling can read each page and set it into its matching Woody snippet on the live site.

Publishing to the live site is always human reviewed: files here are staged, then applied to Woody snippets one page at a time, with a backup of the current live snippet taken first.
