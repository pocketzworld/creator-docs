# **How to Collaborate to Create a Document in Creator Studio**

## **Introduction**

Collaboration is a key aspect of working on projects with multiple team members. In Creator Studio, you can collaborate with others to create and edit documents, scripts, and other assets. This guide will walk you through the process of collaborating on a document in Creator Studio.

## **What is Collaboration in Creator Studio?**

Collaboration in Creator Studio refers to the ability to work together with other team members on the same document. It allows multiple users to make changes, provide feedback, and track revisions in real-time. This feature is especially useful for teams working remotely.

## **How to Collaborate on a Document in Creator Studio**

> Make sure you read [this guide](https://create.highrise.game/learn/studio/guides/collaboration/github) on how to use GitHub for collaboration.

To collaborate on a document in Creator Studio, follow these steps:

## Collaborating Locally with Git
Collaborating locally involves cloning the repository to your local machine, making changes, and pushing them back to GitHub **(recommended for advanced users)**. Follow these steps to collaborate locally with Git:

> Make sure you have Git installed on your local machine. If not, you can download it from the [official Git website](https://git-scm.com/).

### Step 1: Navigate to the GitHub Repository
- [Click here](https://github.com/pocketzworld/creator-docs) to access the Creator Studio documentation repository on GitHub.

### Step 2: Create a Fork
- Click on the "Fork" button in the top right corner of the repository page to create a copy of the repository in your GitHub account.
- Give your fork a name and description(optional) and click on "Fork repository."

### Step 3: Clone the Repository
- Open your forked repository on GitHub and click on the "Code" button.
- Copy the **HTTPS** or **SSH** link provided.
- Create a new folder on your local machine and open a terminal window.
- Run the following command to clone the repository to your local machine:
  ```bash
  git clone <repository_link>
  ```
  Replace `<repository_link>` with the link you copied from GitHub.

### Step 4: Create a New Branch
- Navigate to the cloned repository on your local machine using the terminal `cd <repository_name>`.
- In the terminal, create a new branch for your changes:
  ```bash
  git checkout -b <branch_name>
  ```
  Replace `<branch_name>` with a descriptive name for your branch.

### Step 5: Make Changes
- Open the document you want to collaborate on in Creator Studio.
- Make your edits, add content, or suggest revisions.
- Save your changes in Creator Studio `File > Save` or `Ctrl + S`.

### Step 6: Commit Your Changes
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

### Step 7: Create a Pull Request

- Go to your forked repository on GitHub (e.g., https://github.com/your_username/creator-docs).
- Click on the "Pull Request" button.
- Select the base repository (`pocketzworld/creator-docs`) and the branch you want to merge your changes into.
- Add a title and description for your pull request.
- Carefully review your changes.
- Click on "Create Pull Request" to submit your changes for review.

### Step 8: Review

- Wait for feedback from other collaborators.
- Address any comments or suggestions.

### Tutorial Video

<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/ah5HTQM_TzA" title="YouTube Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Collaborating in GitHub Web Interface
Collaborating directly in the GitHub web interface is another way to work on documents in Creator Studio. Follow these steps to collaborate in the GitHub web interface:

### Step 1: Navigate to the Document

- Go to the document you want to collaborate on.
- Top right corner, click on the "Edit" button.
- This will open the document in the GitHub web interface editor.

### Step 2: Fork the Repository

- If you haven't already, fork the repository by clicking on the "Fork" button in the top right corner of the repository page.

### Step 3: Make Changes

- Click on the pencil icon to edit the document directly in the GitHub web interface.
- Add content, make revisions, or suggest changes.
- Once you're done, click on "Preview" to see how your changes will look.

### Step 4: Commit Changes

- Click on the "Commit changes" button to save your edits.
- Add a title and description for your changes.
- Click on the "Propose changes" button to commit your changes.

### Step 5: Create a Pull Request

- After committing your changes, GitHub will prompt you to create a pull request.
- Add a title and description for your pull request.
- Review your changes and click on the "Create pull request" button.

### Step 6: Review and Merge

- Wait for feedback from other collaborators.
- Address any comments or suggestions.

> **Note:** If you're collaborating in the GitHub web interface, you can skip the steps related to cloning the repository and working locally.

## Conclusion

Collaborating on documents in Creator Studio is a seamless process that allows multiple team members to work together efficiently. By following the steps outlined in this guide, you can contribute to projects, provide feedback, and track revisions effectively. Embrace collaboration to enhance your workflow and create outstanding content in Creator Studio. Happy collaborating 🚀!