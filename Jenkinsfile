pipeline {

  agent any

  options {

    buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')

  }

  stages {

   stage('Test') {
      steps {
       withCredentials([
	conjurSecretCredential(credentialsId: 'DemoVault-CICD-CICD_Secrets-MySQL-username', variable: 'DB_UNAME'),
        conjurSecretCredential(credentialsId: 'DemoVault-CICD-CICD_Secrets-MySQL-password', variable: 'DB_PWD')
	]) {
		sh "echo ######## >> /demo/demo.out"
		sh "echo 'Multi-Branch pipeline:' >> /demo/demo.out"
		sh "date >> /demo/demo.out"
		sh "echo Test: >> /demo/demo.out"
		sh "echo DB_UNAME=$DB_UNAME >> /demo/demo.out"
		sh "echo DB_PWD=$DB_PWD >> /demo/demo.out"
		sh "echo >> /demo/demo.out"
       }
     }
   }

   stage('Prod') {
     steps {
       withCredentials([
	conjurSecretCredential(credentialsId: 'DemoVault-CICD-CICD_Secrets-MSSQLserver-username', variable: 'DB_UNAME'),
        conjurSecretCredential(credentialsId: 'DemoVault-CICD-CICD_Secrets-MSSQLserver-password', variable: 'DB_PWD')
	]) {
		sh "echo Prod: >> /demo/demo.out"
		sh "echo DB_UNAME=$DB_UNAME >> /demo/demo.out"
		sh "echo DB_PWD=$DB_PWD >> /demo/demo.out"
		sh "echo ######## >> /demo/demo.out"
       }
     }
   }

   stage('Results') {
     steps (
       echo "Finished!"
     }
   }
  }
}
