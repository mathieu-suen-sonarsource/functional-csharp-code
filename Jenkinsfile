node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def msbuildHome = tool "sonarscanner"
    withSonarQubeEnv() {
      sh "dotnet ${msbuildHome}/SonarScanner.MSBuild.dll  begin /k:\"functional-csharp-code\""
      sh "dotnet build ."
      sh "dotnet ${msbuildHome}/SonarScanner.MSBuild.dll  end"
    }
  }
}
