pipeline {
  agent any
  stages {
    stage('jj') {
      parallel {
        stage('jj') {
          steps {
            timeout(time: 2, activity: true) {
              node(label: 'j') {
                isUnix()
              }

            }

            writeFile(file: 'aa', text: 'bb')
            stash(name: 'aastash', includes: 'aa')
          }
        }

        stage('jjP') {
          steps {
            writeFile(file: 'aa', text: 'cc')
            writeFile(file: 'bb', text: 'aa')
            stash(name: 'aa', includes: '*')
          }
        }

      }
    }

    stage('f') {
      steps {
        archiveArtifacts(artifacts: '*', allowEmptyArchive: true, defaultExcludes: true, fingerprint: true, onlyIfSuccessful: true)
      }
    }

  }
}