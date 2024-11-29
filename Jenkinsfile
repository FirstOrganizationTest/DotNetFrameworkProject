node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def msbuildHome = tool 'Default MSBuild'
    def scannerHome = tool 'SonarScanner for .NET'

      bat "\"${scannerHome}\\SonarScanner.MSBuild.exe\" begin /k:\"DotNetFrameworkProject\" /d:sonar.verbose=true /d:sonar.host.url=\"http://localhost:1007\" /d:sonar.token=\"\""
      bat "\"${msbuildHome}\\MSBuild.exe\" DotNetFrameworkProject.sln /t:Rebuild"
      bat "\"${scannerHome}\\SonarScanner.MSBuild.exe\" end /d:sonar.token=\"\""    
  }
}
