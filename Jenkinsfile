pipeline {

  agent any

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
		sh "echo Prod:"
                sh "echo -n DB_UNAME="
                sh "echo $DB_UNAME | sed 's/./& /g'"
                sh "echo -n DB_PWD="
                sh "echo $DB_PWD | sed 's/./& /g'"
		sh "echo ########"
       }
     }
   }
 }
}
