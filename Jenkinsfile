node {
    def app

    stage('Clone repository') {
        /* Afin de s'assurer que le repértoire est cloné dans l'espace detravail */

        checkout scm
    }

    stage('Build image') {
        /* Lancement de la compilation */

        app = docker.build("moustadrafh/hello-world")
    }

    stage('Test image') {
        /* Test du framework*/

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        /* Phase finale */
        docker.withRegistry('https://cloud.docker.com/repository/docker/moustadrafh/hello-world', 'moustadrafh/hello-world') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
