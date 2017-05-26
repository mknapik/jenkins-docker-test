node('docker') {
    withCleanup {
        checkout scm

        def myEnv = docker.build 'jenkins-docker-test:latest'
        myEnv.inside {
           sh 'bundle exec rake --version'
        }
    }
}
