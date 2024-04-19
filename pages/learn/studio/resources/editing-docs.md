# **How to Make Changes to Documentation**

## **Introduction**

Anyone can make changes or create new guides and documentation on the creator portal. This guides walks you through the steps required.

## Option 1: Making Changes via the Web Interface
Making changes directly in the GitHub web editor is the easiest way to make edits to the documentation. Follow these steps:

### 1: Navigate to the Document

- Go to the document you want to edit.
- Top right corner, click on the "Edit" button.
- This will open the document in the GitHub web interface editor.

### 2: Fork the Repository

- If you haven't already, fork the repository by clicking on the "Fork" button in the top right corner of the repository page.

### 3: Make Changes

- Click on the pencil icon to edit the document directly in the GitHub web interface.
- Add content, make revisions, or suggest changes.
- Once you're done, click on "Preview" to see how your changes will look.

### 4: Commit Changes

- Click on the "Commit changes" button to save your edits.
- Add a title and description for your changes.
- Click on the "Propose changes" button to commit your changes.

### 5: Create a Pull Request

- After committing your changes, GitHub will prompt you to create a pull request.
- Add a title and description for your pull request.
- Review your changes and click on the "Create pull request" button.

### 6: Review and Merge

- Wait for feedback from reviewers.
- Address any comments or suggestions.

## Option 2: Making Changes Locally with Git
Making Changes locally involves cloning the repository to your local machine, making changes, and pushing them back to GitHub **(recommended for advanced users)**. Follow these steps to make changes locally with Git:

> Make sure you have Git installed on your local machine. If not, you can download it from the [official Git website](https://git-scm.com/).

### 1: Navigate to the GitHub Repository
- [Click here](https://github.com/pocketzworld/creator-docs) to access the Creator Studio documentation repository on GitHub.

### 2: Create a Fork
- Click on the "Fork" button in the top right corner of the repository page to create a copy of the repository in your GitHub account.
- Give your fork a name and description(optional) and click on "Fork repository."

### 3: Clone the Repository
- Open your forked repository on GitHub and click on the "Code" button.
- Copy the **HTTPS** or **SSH** link provided.
- Create a new folder on your local machine and open a terminal window.
- Run the following command to clone the repository to your local machine:
  ```bash
  git clone <repository_link>
  ```
  Replace `<repository_link>` with the link you copied from GitHub.

### 4: Create a New Branch
- Navigate to the cloned repository on your local machine using the terminal `cd <repository_name>`.
- In the terminal, create a new branch for your changes:
  ```bash
  git checkout -b <branch_name>
  ```
  Replace `<branch_name>` with a descriptive name for your branch.

### 5: Make Changes
- Open the document you want to edit.
- Make your edits, add content, or suggest revisions.
- Save your changes `File > Save` or `Ctrl + S`.

### 6: Commit Your Changes
- #### If you are using the terminal
  - In the terminal, add the changes to the staging area:
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
  Replace `<branch_name>` with the name of your branch.

- #### If you are using VS Code
  - Open the source control tab.
  - Click on the `+` icon to stage all changes.
  - Enter a commit message and click on the checkmark icon to commit the changes.
  - Click on the three dots icon and select "Push" to push the changes to your forked repository.

### 7: Create a Pull Request

- Go to your forked repository on GitHub (e.g., https://github.com/your_username/creator-docs).
- Click on the "Pull Request" button.
- Select the base repository (`pocketzworld/creator-docs`) and the branch you want to merge your changes into.
- Add a title and description for your pull request.
- Carefully review your changes.
- Click on "Create Pull Request" to submit your changes for review.

### 8: Review

- Wait for feedback from reviewers.
- Address any comments or suggestions.

### Tutorial Video

<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/ah5HTQM_TzA" title="YouTube Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
