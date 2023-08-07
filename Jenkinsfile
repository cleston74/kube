pipeline {
  agent any
  stages {
    stage('Fase 1') {
      steps {
        echo 'Fase 1'
      }
    }

    stage('Fase 2') {
      steps {
        script {
          pipeline {
            agent any;
            stages {
              stage("parallel") {
                steps {
                  script {
                    def j=[:]
                    [
                      [name: "api", folder: "api"],
                      [name: "ui", folder: "ui"]
                    ].each { m ->
                    j[m.name] = {
                      stage('a') {
                        echo "A"
                      }
                      stage('b') {
                        echo "B"
                      }
                    }
                  }
                  parallel j
                }
              }
            }
          }
        }
      }

    }
  }

  stage('Final') {
    steps {
      echo 'Finalizado'
    }
  }

}
}