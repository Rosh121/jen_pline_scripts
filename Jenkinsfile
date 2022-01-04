String branchName = "main"
String repoUrl = "https://github.com/Rosh121/java_cases.git"

node {
  // Start Stages
  stage('Clone') {
      // Clones the repository from the current branch name
      echo 'Clean the output directory if exists'
      bat(/cd "C:\ProgramData\Jenkins\.jenkins\workspace\gs-maven"
          if test -d "build";
          then rmdir \/s \/q "build";
          else mkdir "build";
          fi/)

      echo 'Cloning files from (branch: "' + branchName + '" )'
      dir('build') {
          git branch: branchName, url: repoUrl
      }
  }
}
