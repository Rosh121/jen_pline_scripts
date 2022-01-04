String branchName = "main"
String repoUrl = "https://github.com/Rosh121/java_cases.git"

node {
  // Start Stages
  stage('Clean and Clone') {
      // Clones the repository from the current branch name
      echo 'Clean the output directory if exists'
      bat(/cd "C:\ProgramData\Jenkins\.jenkins\workspace\gs-maven"
          if exist "build\" rmdir \/s \/q "build"
          mkdir "build"
          echo 'cleaning done'/)

      echo 'Cloning files from (branch: "' + branchName + '" )'
      dir('build') {
          git branch: branchName, url: repoUrl
      }
  }
}
