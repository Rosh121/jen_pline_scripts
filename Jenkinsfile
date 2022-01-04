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
  stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      // git $repoUrl
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.
      mvnHome = tool 'M3'
  }
  stage('Build') {
      // Run the maven build
      withEnv(["MVN_HOME=$mvnHome"]) {
          if (isUnix()) {
              sh '"$MVN_HOME/bin/mvn" -Dmaven.test.failure.ignore clean package'
          } else {
              bat(/"%MVN_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean package/)
          }
      }
  }
  stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
  }
}
