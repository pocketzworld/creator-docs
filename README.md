This repository contains the source code for the Highrise Creator documentation available at [create.highrise.game/learn](https://create.highrise.game/learn).

If you're not sure about the process of contributing through GitHub, please refer to [About pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) and the following video.

## Contribution Guidelines

All additions to Highrise Creator documentation need to align with our existing approach and standards and should be applicable to a wide range of experiences and use cases.

When submitting a pull request for review, please agree to the conditions listed below:

- This contribution was created in whole or in part by me, and I have the right to submit it under the terms of this repository's open source licenses.
- I understand and agree that this contribution and a record of it are public, maintained indefinitely, and may be redistributed under the terms of this repository's open source licenses.
- To the best of my knowledge, all proposed changes are accurate.

## File Types

Highrise Creator documentation primarily contains three types of documents:

- Guides and tutorials are placed in `.md` files in [pages](./pages)

  These documents are often tutorial or guide based and should use a friendly and conversation driven tone. Information should be easy to understand, brief, and directly to the point. If the contents appear lengthy, consider dividing information over multiple pages.

- LUA API reference documents can be found in `.yaml` files in [pages](./pages)

  API elements like classes, enums, etc. should have documentation in YAML files. For reference, check

- Navigation and structure is defined in `_meta.json`

  This file defines the navigation structure of the documentation (order and titles). Routing is handled automatically based on directory structure. If you want to add a new page, you need to add a new entry to `_meta.json` in the following format:

  ```json
  {
    "page_name": 
      {
        "title": "Page Title",
        "redirectTo(optional)": "path"
      }
  }
  ```

- Assets are saved as `.png` and `.jpg` files in [assets](./assets)
  
  These files are used to illustrate the documentation and should be saved in the highest possible resolution. Aim for less than 200kb per image. Maximum displayed image width is 724px, for HiDPI displays, images should be at least 1448px wide.

If your contribution focuses on a very specific topic, it may not be suitable for the documentation. In such cases, consider sharing your content on the [Highrise Create forum](https://createforum.highrise.game/).
