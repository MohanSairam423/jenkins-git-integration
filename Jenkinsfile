pipeline {
    agent any
    
    stages {
		stage("Build") {
			steps {
				echo "BUILD"	
				snDevOpsSonar(name:'LocalSonar', projectKey:'github-jenkins-sonar')
			}
		}
		stage("Code Quality") {
			steps {
			 	withSonarQubeEnv('LocalSonar') {
					sh '/Applications/SonarScanner/bin/sonar-scanner -Dproject.settings=/Applications/sonar-scanner.properties'
					sh 'env'
              			}
				snDevOpsSonar(name:'LocalSonar', projectKey:'github-jenkins-sonar')
				//sh 'env'
			}
		}
		stage("UAT") {
			steps {
				echo "UAT"
				snDevOpsSonar(name:'LocalSonar', projectKey:'github-jenkins-sonar')
			}
		}
		stage("Prod") {
			steps {
				echo "PROD"
				withSonarQubeEnv('LocalSonar') {
					sh '/Applications/SonarScanner/bin/sonar-scanner -Dproject.settings=/Applications/sonar-scanner.properties'
					sh 'env'
              			}
				snDevOpsSonar(name:'LocalSonar', projectKey:'github-jenkins-sonar')
			}
		}
	}
}
