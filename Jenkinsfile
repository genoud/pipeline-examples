pipeline {
    agent { 
        docker { 
            image 'genoud6/sfdx-ci:v1.2'
            args '-u root'
        } 
    }
	node{
		properties([parameters([string(name: 'TEST_PARAM', defaultValue: 'master')])])
		echo "Test Param: ${TEST_PARAM}"

	}
    stages {
        stage('build') {
            steps {
                sh 'npm --version'
                sh 'java -version'
                sh 'ant -version'
                sh 'sfdx --version'
            }
        }
        stage('test') {
            steps {
                sh 'echo run test'
            }
        }
        stage('analyse') {
            steps {
                script {
                    // some block

                    def reportExist= fileExists 'report'
                    if(reportExist==false){
                        sh 'mkdir report'
                    }
                    
                    sh returnStatus: true, script: 'pmd -d force-app -l apex -reportfile report/output.csv -f csv -R config/ruleset.xml'
                    sh returnStatus: true, script: 'pmd -d force-app -l apex -reportfile report/output.xml -f xml -R config/ruleset.xml'
                    pmd canComputeNew: false, canRunOnFailed: true, defaultEncoding: '', healthy: '', pattern: 'report/output.xml', unHealthy: ''
                }
                
            }
        }
    }
}