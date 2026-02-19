# Assignment (Optional)

## Brief

Practice GitHub branching workflow and collaboration using Git commands to simulate a DevOps team environment.

1. **GitHub Branching and Pull Request Workflow**
   - Use an existing GitHub repository (create a new one if needed)
   - Clone the repository to your local machine:
```bash
     git clone <repository-url>
```
   - Create a new feature branch from main:
```bash
     git branch feature-yourname-readme
     git checkout feature-yourname-readme
```
   - Make changes to the project:
     - Create or update a README.md file
     - Add your name and a brief description of what the project does
     - Add at least 2-3 sentences explaining a feature
   - Stage and commit your changes:
```bash
     git add .
     git commit -m "Update README with project description"
```
   - Push your feature branch to GitHub:
```bash
     git push origin feature-yourname-readme
```
   - Create a pull request on GitHub:
     - Go to your repository on GitHub
     - Click "Compare & pull request"
     - Add a descriptive title and description
     - Create the pull request (do not merge yet)
   - Take a screenshot showing your pull request
   - Merge the pull request into main
   - Delete the feature branch after merging

2. **Practice Essential Git Commands**
   - After merging your pull request, practice the following Git commands and document what each command does:
   - Update your local main branch:
```bash
     git checkout main
     git pull origin main
```
   - View commit history:
```bash
     git log
```
   - Create a new branch and make a small change (e.g., add a new file called `notes.txt` with some text)
   - Use `git status` to check which files are modified
   - Use `git diff` to see the exact changes before committing
   - Stage, commit, and push your changes
   - Write a brief summary (3-4 sentences) explaining:
     - The difference between `git fetch` and `git pull`
     - Why branching is important in DevOps workflows
     - How pull requests support collaboration and code quality

## Submission (Optional)

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.

## References
- Java: https://docs.oracle.com/javase/
- Spring Boot: https://docs.spring.io/spring-boot/docs/current/reference/html/
- PostgreSQL: https://www.postgresql.org/docs/
- OWASP: https://cheatsheetseries.owasp.org/