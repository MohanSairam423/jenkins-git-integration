pipeline {
    agent any
    
    stages {
		stage("Build") {
			steps {
				echo "BUILD"
			}
		}
		stage("Code Quality") {
			steps {
			 	withSonarQubeEnv('LocalSonar') {
					sh '/Applications/SonarScanner/bin/sonar-scanner -Dproject.settings=/Applications/sonar-scanner.properties'
					//sh 'env'
              			}
				snDevOpsSonar(name:'LocalSonar', projectKey:'github-jenkins-sonar')
				//sh 'env'
			}
		}
		stage("UAT") {
			steps {
				echo "UAT"
				sleep 10
				snDevOpsSonar(name:'LocalSonar', projectKey:'github-jenkins-sonar')
			}
		}
		stage("Prod") {
			steps {
				echo "PROD"
				withSonarQubeEnv('LocalSonar') {
					sh '/Applications/SonarScanner/bin/sonar-scanner -Dproject.settings=/Applications/sonar-scanner.properties'
					//sh 'env'
              			}
				snDevOpsSonar(name:'LocalSonar', projectKey:'github-jenkins-sonar')
			}
		}
	}
}
