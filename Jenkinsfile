pipeline {
    environment {
        TOKEN = credentials('SURGE_TOKEN')
      }
    agent {
        docker { image 'node:8'
        args '-u root:root'
        }
    }
    stages {
        stage('Clone') {
            steps {
                git branch:'master',url:'https://github.com/oscarsanabria80/ic-html5'
            }
        }


        
        stage('Install surge')
        {
            steps {
                sh 'npm install --global surge'
            }
        }
        stage('Deploy')
        {
            steps{
                sh 'surge ./_build/ oscarsanabria80.surge.sh --token $TOKEN'
            }
        }
        
    }
}
