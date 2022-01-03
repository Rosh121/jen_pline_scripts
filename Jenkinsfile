String branchName = "main"
String repoUrl = "https://github.com/Rosh121/java_cases.git"

node {
  // Start Stages
  stage('Clone') {
      // Clones the repository from the current branch name
      echo 'Make the output directory'
      bat(/mkdir "build2"/)

      echo 'Cloning files from (branch: "' + branchName + '" )'
      dir('build2') {
          git branch: branchName, url: repoUrl
      }
  }
}
