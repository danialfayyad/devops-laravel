node {
    checkout scm

    stage("Build") {
        sh '''
        apt update
        apt install -y composer
        composer install || true
        '''
    }

    stage("Testing") {
        sh 'echo "Ini adalah test"'
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