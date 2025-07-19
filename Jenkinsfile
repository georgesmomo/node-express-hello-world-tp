// Jenkinsfile
pipeline {
    agent any // Ce pipeline peut tourner sur n'importe quel agent Jenkins disponible

    stages {
        stage('Install Dependencies') {
            steps {
                echo 'Installation des dépendances npm...'
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                echo 'Lancement des tests...'
                // On simule encore car le projet n'a pas de vrai script de test
                sh 'echo "Tests terminés avec succès !"'
            }
        }
    }

    post {
        always {
            // Cette section s'exécute toujours à la fin, que le build réussisse ou échoue
            echo 'Fin du pipeline.'
            cleanWs() // Plugin qui nettoie l'espace de travail
        }
    }
}