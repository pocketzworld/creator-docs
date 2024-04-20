# How to Make Changes to Documentation

This guide walks you through the steps to make changes or create new guides and documentation on the creator portal.

## Option 1: Making Changes via the Web Interface

Follow these steps to make edits to the documentation directly in the GitHub web editor:

1. Navigate to the document you want to edit.
2. Click on the "Edit" button in the top right corner to open the document in the GitHub web interface editor.
3. If you haven't already, fork the repository by clicking on the "Fork" button in the top right corner of the repository page.
4. Click on the pencil icon to edit the document directly in the GitHub web interface.
5. Add content, make revisions, or suggest changes.
6. Click on "Preview" to see how your changes will look.
7. Click on the "Commit changes" button to save your edits.
8. Add a title and description for your changes.
9. Click on the "Propose changes" button to commit your changes.
10. After committing your changes, GitHub will prompt you to create a pull request.
11. Add a title and description for your pull request.
12. Review your changes and click on the "Create pull request" button.
13. Wait for feedback from reviewers and address any comments or suggestions.

## Option 2: Making Changes Locally with Git

Follow these steps to make changes locally with Git (recommended for advanced users):

1. Navigate to the [Creator Studio documentation repository on GitHub](https://github.com/pocketzworld/creator-docs).
2. Click on the "Fork" button in the top right corner of the repository page to create a copy of the repository in your GitHub account.
3. Open your forked repository on GitHub and click on the "Code" button.
4. Copy the HTTPS or SSH link provided.
5. Create a new folder on your local machine and open a terminal window.
6. Run the following command to clone the repository to your local machine:

   ```bash
   git clone <repository_link>
   ```

7. Navigate to the cloned repository on your local machine using the terminal:

   ```bash
   cd <repository_name>
   ```

8. In the terminal, create a new branch for your changes:

   ```bash
   git checkout -b <branch_name>
   ```

9. Open the document you want to edit, make your changes, and save the file.
10. Commit your changes:
    - If using the terminal:
      - Add the changes to the staging area:

        ```bash
        git add .
        ```

      - Commit the changes with a descriptive message:

        ```bash
        git commit -m "Your commit message here"
        ```

      - Push the changes to your forked repository on GitHub:

        ```bash
        git push origin <branch_name>
        ```

    - If using VS Code:
      - Open the source control tab.
      - Click on the `+` icon to stage all changes.
      - Enter a commit message and click on the checkmark icon to commit the changes.
      - Click on the three dots icon and select "Push" to push the changes to your forked repository.
11. Go to your forked repository on GitHub.
12. Click on the "Pull Request" button.
13. Select the base repository (`pocketzworld/creator-docs`) and the branch you want to merge your changes into.
14. Add a title and description for your pull request.
15. Review your changes and click on "Create Pull Request" to submit your changes for review.
16. Wait for feedback from reviewers and address any comments or suggestions.

### Tutorial Video

<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/ah5HTQM_TzA" title="YouTube Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
