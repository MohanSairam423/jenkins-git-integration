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
              			}
				sh 'env'
			}
		}
		stage("UAT") {
			steps {
				echo "UAT"	
			}
		}
		stage("Prod") {
			steps {
				echo "PROD"	
			}
		}
	}
}
