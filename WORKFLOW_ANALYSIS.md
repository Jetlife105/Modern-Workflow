WorkFlow_analysis answers 

1. What triggers this workflow to run?

The workflow automatically runs when code is pushed to the main branch or when a pull request targeting the main branch is opened or updated. This allows GitHub Actions to test changes before they are merged. However, the website is only deployed when changes are pushed to main, not when a pull request is created.

2. What are the four main steps this workflow performs?

The four main steps in the build-and-test job are

Checkout code: Retrieves the repository files.

Validate HTML: Checks the website's HTML files for errors.

Check links: Checks for broken links in the project.

Upload artifact: Uploads the website files so they can be used for deployment.

After these steps, a separate deployment job publishes the website to GitHub Pages when the required conditions are met.

3. What does the "Checkout code" step do, and why is it necessary?

The Checkout code step uses actions/checkout@v4 to download the repository's code into the GitHub Actions environment. This is necessary because the workflow needs access to the website files before it can validate the HTML, check links, and prepare the website for deployment. Without this step, the workflow would not have the project files available to work with.

4. What is the purpose of the environment configuration?

The environment configuration tells GitHub Actions that the website will be deployed to the GitHub Pages environment. It also provides the URL of the deployed website. The workflow includes permissions that allow GitHub Actions to publish the website securely. This helps organize the deployment process and makes it easier to track where the website is published.

5. How does this automated deployment improve reliability compared to manual deployment?

Automated deployment improves reliability by making the process more consistent and reducing the likelihood of human error. Instead of manually uploading files every time changes are made, GitHub Actions automatically runs checks and prepares the website for deployment. The workflow validates HTML and checks links before publishing. The HTML validation must succeed, while the link-checking step is configured to allow the workflow to continue even if it fails. Overall, this saves time and helps developers catch problems before updating the live website.

6. What would happen if you pushed code to a different branch (not main)?

If I pushed code directly to a different branch, the workflow would not automatically run because its push trigger is configured for the main branch. However, if I created a pull request from that branch into main, the workflow would run the build-and-test job to check the changes. The website would not be deployed from that pull request. Deployment would only happen after the changes were merged or otherwise pushed to the main branch and the required build-and-test job succeeded.
