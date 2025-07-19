pipeline {
    agent any

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['staging', 'production'], description: 'Choisir l\'environnement de déploiement')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Lancer les tests ?')
        string(name: 'APP_VERSION', defaultValue: '1.0.0', description: 'Version de l\'application')
    }

    stages {
        stage('Build Info') {
            steps {
                echo "Déploiement de la version ${params.APP_VERSION} sur l'environnement : ${params.ENVIRONMENT}"
            }
        }

        stage('Test') {
            when {
                expression { return params.RUN_TESTS }
            }
            steps {
                echo "Lancement des tests..."
            }
        }
    }
}