node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def msbuildHome = tool 'Default MSBuild'
    def scannerHome = tool 'SonarScanner for MSBuild'
    withSonarQubeEnv() {
      bat "dotnet sonarscanner begin /k:\"functional-csharp-code\""
      bat "dotnet build ."
      bat "dotnet sonarscanner end"
    }
  }
}
