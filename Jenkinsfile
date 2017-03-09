pipeline {
  agent any
  stages {
    stage('build & unit tests') {
      steps {
        node(label: 'build') {
          sleep(time: 10, unit: 'SECONDS')
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
          sleep(time: 10, unit: 'SECONDS')
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
