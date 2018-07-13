def env_production = 'production'
def env_development = 'development'

pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        deleteDir()
        checkout scm
      }
    }
    stage('Build') {
      steps {
        script {
          sh 'npm install'
          commitChanges()
        }
      }
    }
    stage('Unit Test') {
      steps {
        script {
          sh 'npm test'
        }
      }
    }
  }
}

def commitChanges(){
  sh 'git checkout master'

  if(changes() == ""){
    echo "Nothing changes..."
  } else {
    echo "Commit changes..."
    // sh 'git add --all'
    // sh 'git commit -am RELEASE'
    // sh 'git push origin master'
  }
}

def changes() {
  sh 'git status -s > .git/gitStatus'
  def changes = readFile('.git/gitStatus').trim()
  sh 'rm .git/gitStatus'
  changes
}