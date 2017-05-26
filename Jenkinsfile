node('docker') {
    withCleanup {
        checkout scm

        def myEnv = docker.build 'jenkins-docker-test:latest'
        myEnv.inside {
           sh 'bundle exec rake --version'
           sh 'bundle exec rake'
        }
    }
}

node('docker') {
    withCleanup {
        checkout scm

        withDockerCompose { compose ->
            compose.exec('app', 'bundle exec rake --version')
            compose.exec('app', 'bundle exec rake')
        }
    }
}
