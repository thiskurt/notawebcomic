# Not a Webcomic workflow

See also [the readme](README.md)

For now the `hugo new content --kind` does not seem to work, so instead the workflow is the following:

## Creating a new chapter

Manually create a new chapter folder under `content/comic/[CHAPTER_ID]` and an index file under `content/comic/[CHAPTER_ID]/_index.md` with the following frontmatter:

```toml
+++
[[cascade]]
title = '[CHAPTER TITLE]'
chapterID = '[CHAPTER_ID]'

[_build]
render = 'never'
+++
```

- `title`: a human-readable title
- `chapterID`: string id for the chapter, **must be the same as the folder**

This is probably redundant for now:

> To add a new chapter, place a thumbnail image for the chapter in `assets/img/comic` with the filename `[CHAPTER_ID]_thumb.[EXTENSION]`. Then, run:

## Adding a comic page

Every comic page must be added to an existing chapter. To add a comic page do the following.

1. Add the image asset in `assets/img/comic` with the filename `[CHAPTER_ID]_[3-DIGIT-NO].[EXTENSION]`
2. Manually add a page file in `content/comic/[CHAPTER_ID]/[PAGE_NUMBER].md` with the following content:

    ```toml
    +++
    date = 2023-12-03T00:00:00
    hover = 'Add your hover text here.'
    +++

    Write your comic description or transcript here.
    ```

## A note on chapters

Not a Webcomic doesn't use traditional chapters, but I'm using the chapter language for the different recurring series.

Since the template expects continuous chapters the archive page doesn't completely work as expected. It ends up not sorting the page links under the individual chapters/series, but in a global chronological order, causing some issues.

For now I've simplified the Archive page as a simple list until I do a proper theme overhaul.

## A note on Termux

Termux seems to have issue with a 'build lock', but there is a workaround by using this flag: `--noBuildLock`

It also seems to have an issue when I run it in termux itself where it reports the publish directory as readonly, doing it in proot/ubuntu works though.

Maybe don't use dropbox for this one? Or probably the thing to do is to keep the PC, Phone and Tablet ones completely seperate, but for now let's just do this.
