node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def msbuildHome = tool 'Default MSBuild'
    def scannerHome = tool 'SonarScanner for MSBuild'
    withSonarQubeEnv() {
      sh "dotnet tool install --global dotnet-sonarscanner"
      sh "dotnet sonarscanner begin /k:\"functional-csharp-code\" /d:sonar.login=\"3cb4e4a54fd96a46865b1fb1d9e86caed2dacb25\""
      sh "dotnet build ."
      sh "dotnet sonarscanner end /d:sonar.login=\"3cb4e4a54fd96a46865b1fb1d9e86caed2dacb25\""
    }
  }
}
