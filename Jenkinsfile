node {
    stage ('Checkout') {
       checkout scm
    }
    stage ('Build') {
		docker.image('trion/ng-cli').inside {
			sh 'npm install'
			sh 'ng build --progress false --prod --aot'
			sh 'tar -cvzf dist.tar.gz --strip-components=1 dist'
		}
		archive 'dist.tar.gz'
    }
    stage ('Test') {
		docker.image ('trion/ng-cli-karma').inside {
			sh 'ng test --progress false --watch false'
		}
<<<<<<< HEAD
        junit '**/test-results.xml'
=======
>>>>>>> d6a8898e977382ecb26c34d8cca4c98d81fe21da
    }
}