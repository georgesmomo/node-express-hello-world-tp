pipeline {
    agent {
        label 'nodejs' // Tourne sur un agent qui a l'étiquette 'linux' ET 'docker'
    }

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['staging', 'production'], description: 'Choisir l\'environnement de déploiement')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Lancer les tests ?')
        string(name: 'APP_VERSION', defaultValue: '1.0.0', description: 'Version de l\'application')
    }


    stages {
        stage('Check Agent') {
            steps {
                echo "Agent OK : labels = ${env.NODE_LABELS}"
                sh 'whoami && uname -a && docker --version'
            }
        }
        stage('Build Info') {
            steps {
                echo "-----------------------------"
                echo "📦 Version de l'application : ${params.APP_VERSION}"
                echo "🌍 Environnement choisi      : ${params.ENVIRONMENT}"
                echo "🧪 Lancer les tests ?        : ${params.RUN_TESTS}"
                echo "-----------------------------"
            }
        }
        stage('Run inside Pod') {
            steps {
                // Pour exécuter une commande dans le container 'nodejs'
                container('nodejs') { 
                    sh 'node --version'
                    sh 'npm --version'
                }
            }
        }
        stage('Test') {
            when {
                expression { return params.RUN_TESTS }
            }
            steps {
                echo "✅ Lancement des tests automatiques en cours..."
                // Exemple : sh 'npm test' ou autre
            }
        }
    }
}
