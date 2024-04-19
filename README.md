# Highrise Creator Documentation

This repository holds source code for the creator documentation at [create.highrise.game](https://create.highrise.game).

If you're not sure about the process of contributing through GitHub, please refer to [About pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).

**Note**: Currently, the repository has guides, tutorials, educational content, and the Studio API reference. Code samples are coming soon.

## Reporting Issues

If you find a problem with the documentation and don't want to submit a pull request, please let us know by [reporting it on the Highrise creator forums](https://createforum.highrise.game/).

## Contribution Guidelines

All additions to Highrise Creator documentation need to align with our existing approach and standards and should be applicable to a wide range of experiences and use cases.

When submitting a pull request for review, please agree to the conditions listed below:

- This contribution was created in whole or in part by me, and I have the right to submit it under the terms of this repository's open source licenses.
- I understand and agree that this contribution and a record of it are public, maintained indefinitely, and may be redistributed under the terms of this repository's open source licenses.
- To the best of my knowledge, all proposed changes are accurate.

## Minor Contributions

For simple changes that only touch a single file, use GitHub's web-based editor:

1. Find the file in `content/en-us/` and click **Edit this file**.
1. Click **Fork this repository**.
1. Make your changes and click **Commit changes...**.
1. Give your change a descriptive commit message and click **Propose changes**.
1. Ensure that the base repository is `pocketzworld/creator-docs` and the base branch is `main`. Verify that you're happy with your changes and click **Create pull request**.
1. Finally, fill out the details in the pull request description and click **Create pull request**.

## Larger Contributions

For larger changes that touch multiple files, we recommend github.dev, a more full-featured text editor based on Visual Studio Code that runs in your browser:

1. Fork the repository.
1. While browsing your fork, press the <kbd>.</kbd> key to open github.dev.
1. In the **Source Control** menu, click **...** > **Branch** > **Create Branch...**.
1. Give the branch a name and click **Switch to Branch**.
1. Use the **Explorer** menu to find the files you want to update in `content/en-us`, and make your desired changes.
1. In the **Source Control** menu, verify that you're happy with your changes.
1. Add a commit message and click **Commit & Push**.
1. In a new browser tab, navigate to [github.com/pocketzworld/creator-docs](https://github.com/pocketzworld/creator-docs).
1. Click **Compare & pull request**.
1. Verify that the base repository is `pocketzworld/creator-docs` and the base branch is `main`. The head repository should be your fork and your branch.
1. Finally, fill out the details in the pull request description and click **Create pull request**.

Alternatively, you can use the **GitHub** or **GitHub Pull Request** menus in github.dev to submit the pull request. For documentation on using github.dev, see [GitHub Codespaces](https://docs.github.com/en/codespaces/the-githubdev-web-based-editor).

## Offline Workflow

This repository is extremely large, so we recommend using the online options whenever possible. However, if you're already familiar with the general GitHub workflow and want to use an offline text editor, here are the basic steps for contributing to the documentation:

1. Set up [Git](https://docs.github.com/en/get-started/quickstart/set-up-git) and [Git LFS](https://docs.github.com/en/repositories/working-with-files/managing-large-files/installing-git-large-file-storage). Alternatively, install a Git client like [GitHub Desktop](https://desktop.github.com).
1. Fork this repository.
1. Clone your fork.
1. Navigate to the repository root.
1. Create a new branch.
1. Make your desired changes.
1. Commit, push to your fork, and submit your pull request against this repository's `main` branch.

For more detailed steps, see [CONTRIBUTING.md](CONTRIBUTING.md).

## Document Types

The Highrise documentation has three main document types:

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

If your contribution doesn't fit within these categories or covers a particularly narrow subject, it might not be a good fit for the documentation. Consider posting it to the [Highrise creator forum](https://createforum.highrise.game/).

## Contribution Basics

Try to limit your edits to one class or feature so that the pull request is easier to review. Bug fixes and smaller improvements have a higher likelihood of fast approval. Large guides often require significant back-and-forth before publication.

To avoid formatting issues, we recommend text editors like github.dev that let you preview Markdown as you write it. For prose, try to follow the guidelines in [STYLE.md](STYLE.md). For code samples, use the [LUASTYLE.md](LUASTYLE.md).

To view a page fully formatted per what we see on the `main` branch, use a markdown visualizer tool like [markdown visualizer](https://markdownlivepreview.com/).

## Licenses

- For prose, this project uses the Creative Commons Attribution 4.0 International Public License. For full license text, see [LICENSE](LICENSE).
- Code samples are available under the MIT License. For full license text, see [LICENSE-CODE](LICENSE-CODE).
