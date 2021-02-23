node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    withSonarQubeEnv() {
     
      sh "dotnet sonarscanner begin /k:\"functional-csharp-code\""
      sh "dotnet build ."
      sh "dotnet sonarscanner end"
    }
  }
}
