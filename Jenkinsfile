node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def msbuildHome = tool "sonarscanner"
    withSonarQubeEnv() {
      sh "echo `ls -al ${msbuildHome}`"
      sh "dotnet tool list -g"
      sh "export DOTNET_ROOT=/usr/share/dotnet/"
      sh "echo $$DOTNET_ROOT"
      sh "dotnet sonarscanner begin /k:\"functional-csharp-code\""
      sh "dotnet build ."
      sh "dotnet sonarscanner end"
    }
  }
}
