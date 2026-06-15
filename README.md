# CI/CD Pipeline for HouseRentingSystem (ASP.NET Core MVC)

This repository contains the SoftUni **HouseRentingSystem** ASP.NET Core MVC application. It includes a fully configured Continuous Integration (CI) workflow using **Jenkins** to automate building, restoring, and testing the application.

---

## Step 1: Local Verification
Before uploading code to the repository, it is best practice to ensure the project builds and runs properly locally.

Open the **Package Manager Console** in Visual Studio and run:

```bash
# Build the application
dotnet build

# Run unit and integration tests
dotnet test
```

---

## Step 2: GitHub Repository Setup
Initialize the local Git repository, apply `.gitignore`, and push the application code to GitHub using the Bash CLI:

```bash
# Initialize local repo
git init

# Add .gitignore
dotnet new gitignore

# Stage and commit all files
git add .
git commit -m "Initial commit"

# Link and push to GitHub
git branch -M main
git remote add origin https://github.com {repo}
git push -u origin main
```

---

## Step 3: Jenkins Configuration

1. Open the Jenkins dashboard and click **New Item**.
2. Select **Pipeline**, give it a name (e.g., `HouseRentingSystem-CI`), and click **OK**.
3. In the **General** section, check **GitHub project** and enter your repository URL.
4. Under the **Pipeline** section:
   * Set Definition to **Pipeline script from SCM**.
   * Set SCM to **Git**.
   * Repository URL: Paste your GitHub repository URL.
   * Script Path: `Jenkinsfile`.
5. Click **Save**.

---

## Step 4: Jenkinsfile (The CI Pipeline)
The repository includes a `Jenkinsfile` at the root directory containing the following standard declarative stages:

* **Restore:** Downloads all necessary NuGet packages and project dependencies.
* **Build:** Compiles the project using MSBuild/dotnet to check for syntax and compilation errors.
* **Test:** Executes all unit and integration tests automatically.

---

## Step 5: Testing the Pipeline
1. Go to your Jenkins Job dashboard.
2. Click **Build Now** to trigger the pipeline manually.
3. Click on the build number and select **Console Output** to monitor the build progress and test results in real-time.
