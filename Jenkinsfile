pipeline
{
	agent any
	stages{
		stage('Build Application'){
			steps{
				bat 'mvn clean install'
				}
		}
		
		stage('Munit Testing Application'){
			steps{
				bat 'mvn test'
				}
		}
		
		stage('Deploy Application to Mulesoft Cloudhub'){
			steps{
				bat 'mvn package deploy -DmuleDeploy'
				}
		}
		
		
	}
	 post {
        always {
            emailext body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}", 
            recipientProviders: [[$class: 'DevelopersRecipientProvider'], 
            [$class: 'RequesterRecipientProvider']], 
            subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
        	}
       	}
}