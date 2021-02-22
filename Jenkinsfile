node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    withSonarQubeEnv() {
      bat "dotnet sonarscanner begin /k:\"functional-csharp-code\""
      bat "dotnet build ."
      bat "dotnet sonarscanner end"
    }
  }
}
