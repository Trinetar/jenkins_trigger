pipeline{
	agent any
	
	tools{
	maven "MAVEN3"
	jdk "OracleJDK11"
	}
	
	stages{
		stage('fetch code'){
		steps {
		git branch: 'main', url: 'https://github.com/Trinetar/vprofile-project.git'
		
		}
		}
		stage ('Build'){
		steps {
		  sh 'mvn clean install -DskipTests'
		}
		post {
		success {
		echo 'archiving artifacts.'
		archiveArtifacts artifacts: '**/*.war'
		}
		}
		}
		stage ('unit test'){
		steps {
		sh 'mvn test'
		}
		}
		stage ('checkstyle analysis'){
		 steps {
		  sh 'mvn checkstyle:checkstyle'
		 }
		}
		
	}
}