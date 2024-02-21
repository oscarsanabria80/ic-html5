pipeline {
    environment {
        TOKEN = credentials('SURGE_TOKEN')
      }
    agent {
        docker { image 'debian'
        args '-u root:root'
        }
    }
    stages {
        stage('Clone') {
            steps {
                git branch:'master',url:'https://github.com/oscarsanabria80/ic-html5'
            }
        }


        stage('Install npm')
        {
            steps {
                sh 'apt update && apt install -y npm'
            }
        }
        stage('Install surge')
        {
            steps {
                sh 'npm install -g surge'
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
