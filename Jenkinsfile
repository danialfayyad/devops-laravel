node {
    checkout scm

    stage("Build") {
        docker.image('composer:2').inside('-u root') {
            sh 'git config --global --add safe.directory /var/jenkins_home/workspace/laravel-dev3'
            sh 'composer install'
        }
    }

    stage("Testing") {
        docker.image('ubuntu').inside('-u root') {
            sh 'echo "Ini adalah test"'
        }
    }

    stage("Deploy") {
        docker.image('agung3wi/alpine-rsync:1.1').inside('-u root') {
            sh 'mkdir -p /tmp/deploy'
            sh 'rsync -rav --delete ./ /tmp/deploy --exclude=.env --exclude=storage --exclude=.git'
            sh 'echo "Deploy berhasil ke folder lokal"'
        }
    }
}