pipeline {
    agent { 
        docker { 
            image 'genoud6/sfdx-ci:v1.2'
            args '-u root'
        } 
    }
	parameters {
        

        //text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'DEPLOY', defaultValue: true, description: 'Automatique deploy')
        string(name: 'DEPLOY_USERNAME', defaultValue: 'g.douanla.djatio@accenture.com', description: 'Enter the deploy username if deploy is true')

        //choice(name: 'DEPLOY_USERNAME', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'DEPLOY_CONSUMERKEY', defaultValue: 'SECRET', description: 'Enter the deployment consumer key if deploy is true')

        file(name: "SECRET", description: "Choose a file to upload")
    }
    stages {
        stage('build') {
            steps {
                sh 'npm --version'
                sh 'java -version'
                sh 'ant -version'
                sh 'sfdx --version'
                echo "Deploy Username: ${DEPLOY_USERNAME}"
                echo "Secret: ${SECRET}"
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

                    

                    //def reportExist= fileExists 'report'
                    //if(reportExist==false){
                    //    sh 'mkdir report'
                    //}
                    
                    echo "Test"
                    
                    //sh returnStatus: true, script: 'pmd -d force-app -l apex -reportfile report/output.csv -f csv -R config/ruleset.xml'
                    //sh returnStatus: true, script: 'pmd -d force-app -l apex -reportfile report/output.xml -f xml -R config/ruleset.xml'
                    //pmd canComputeNew: false, canRunOnFailed: true, defaultEncoding: '', healthy: '', pattern: 'report/output.xml', unHealthy: ''
                    
                }
                
            }
        }
    }
}