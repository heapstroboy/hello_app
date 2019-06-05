// add the following line and replace necessary values if you are not loading the library implicitly
// @Library('my-library@master') _

pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                ex_msbuild 'some/path/to.sln'
            }
        }
    }
}