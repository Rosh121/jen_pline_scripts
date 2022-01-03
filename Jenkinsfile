String branchName = env.BRANCH_NAME
String gitCredentials = "CREDENTIAL_ID"
String repoUrl = "https://github.com/Rosh121/java_cases.git"

node {
  // Start Stages
  stage('Clone') {
      // Clones the repository from the current branch name
      echo 'Make the output directory'
      bat(/mkdir "build"/)

      echo 'Cloning files from (branch: "' + branchName + '" )'
      dir('build') {
          git branch: branchName, credentialsId: 	gitCredentials, url: repoUrl
      }
  }
}
