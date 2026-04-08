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

    stage("Deploy Local") {
        sh '''
        rm -rf laravel-deploy
        mkdir laravel-deploy
        cp -r $(ls -A | grep -v laravel-deploy) laravel-deploy/
        echo "Deploy ke workspace berhasil"
        '''
    }
}