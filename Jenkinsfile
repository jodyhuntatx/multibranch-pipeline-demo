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
		sh "echo ########"
                sh "date"
                sh "echo Test:"
                sh "echo -n DB_UNAME="
                sh "echo $DB_UNAME | sed 's/./& /g'"
                sh "echo -n DB_PWD="
                sh "echo $DB_PWD | sed 's/./& /g'"
                sh "echo"
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
                sh "echo -n DB_UNAME="
                sh "echo $DB_UNAME | sed 's/./& /g'"
                sh "echo -n DB_PWD="
                sh "echo $DB_PWD | sed 's/./& /g'"
		sh "echo ######## >> /demo/demo.out"
       }
     }
   }
 }
}
