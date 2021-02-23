node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def msbuildHome = tool "sonarscanner"
    withSonarQubeEnv() {
      sh "echo `ls -al ${msbuildHome}`"
      sh "dotnet tool list -g"
      sh "ls -al $HOME/.dotnet/tools"
      sh "export DOTNET_ROOT=/usr/share/dotnet/"
      sh "$HOME/.dotnet/tools/dotnet-sonarscanner begin /k:\"functional-csharp-code\""
      sh "dotnet build ."
      sh "$HOME/.dotnet/tools/dotnet-sonarscanner end"
    }
  }
}
