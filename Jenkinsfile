pipeline {     
    agent any     
    stages {         
        stage('Checkout') {             
            steps {                 
                // Checkout the source code from your version control system                 
                git url: 'https://github.com/siddharthTricon/calculator_python', branch: 'master'             
            }         
        }         
        stage('Install Dependencies') {             
            steps {                 
                script {                     
                    // Upgrade pip and install dependencies globally                     
                    sh '''                     
                        /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin -m pip install --upgrade pip                         
                    '''                 
                }             
            }         
        }         
        stage('Run Tests') {             
            steps {                 
                script {                     
                    // Run tests using unittest                     
                    sh 'python test_calculator.py'                 
                }             
            }         
        }     
    }     
    post {         
        always {             
            // Clean up the workspace after the build             
            cleanWs()         
        }         
        success {             
            echo 'Tests passed successfully!'         
        }         
        failure {             
            echo 'Tests failed!'         
        }     
    } 
}
