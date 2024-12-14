pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aarush04/quant-lab-in-a-box.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh '''
                # Use explicit path to the correct Python binary
                /Library/Frameworks/Python.framework/Versions/3.12/bin/python3 -m pip install -r requirements.txt
                '''
            }
        }
        stage('Run Tests') {
            steps {
                sh '''
                # Use explicit path to pytest
                /Library/Frameworks/Python.framework/Versions/3.12/bin/python3 -m pytest tests/
                '''
            }
        }
        stage('Run Backtesting') {
            steps {
                sh '''
                # Use explicit path to run backtesting script
                /Library/Frameworks/Python.framework/Versions/3.12/bin/python3 backtesting/backtest.py
                '''
            }
        }
    }
}