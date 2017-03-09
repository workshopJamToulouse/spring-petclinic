pipeline {
  agent any
  stages {
    stage('build & unit tests') {
      steps {
        withMaven(maven: 'M3') {
          sh 'mvn clean install'
          stash(name: 'toto', includes: 'target/\\*.jar')
        }

      }
    }
    stage('static-analysis') {
      steps {
        node(label: 'build') {
          sleep(time: 10, unit: 'SECONDS')
        }

      }
    }
    stage('acceptance-tests') {
      steps {
        parallel(
          "chrome": {
            node(label: 'build') {
              sleep(time: 10, unit: 'SECONDS')
            }


          },
          "edge": {
            node(label: 'build') {
              sleep(time: 10, unit: 'SECONDS')
            }


          },
          "firefox": {
            node(label: 'build') {
              sleep(time: 10, unit: 'SECONDS')
            }


          }
        )
      }
    }
    stage('staging') {
      steps {
        node(label: 'build') {
          sleep(time: 10, unit: 'SECONDS')
        }

      }
    }
    stage('manual-approval') {
      steps {
        node(label: 'build') {
          input 'go no go ?'
        }

      }
    }
    stage('deploy') {
      steps {
        node(label: 'build') {
          sleep(time: 10, unit: 'SECONDS')
        }

      }
    }
  }
}
