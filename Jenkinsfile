pipeline {
   agent any
    tools {
      maven "Maven"
      jdk "JAVA"
    }
      stages {
          stage('Code'){
              steps{
             git 'https://github.com/13Harsha/M3.git'
                }
          }
          stage('compile'){
              steps{
                  powershell label: '', script: 'mvn clean install'
              }
          }
          stage('Jacoco'){
              steps{
                  jacoco maximumBranchCoverage: '70', maximumClassCoverage: '70', maximumComplexityCoverage: '70', 
                  maximumInstructionCoverage: '70', maximumLineCoverage: '70', maximumMethodCoverage: '70'
                  
              }
          }
           stage('SonarQube analysis') {
                steps{
                    withSonarQubeEnv('SonarQube'){
                powershell label: '', script: 'mvn clean package sonar:sonar'
                }
                }
         }
     }
}
