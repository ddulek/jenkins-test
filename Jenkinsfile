pipeline {
    agent none
    stages {
        stage('Non-Parallel Stage') {
            agent {
                label "maven"
            }
            steps {
                echo 'This stage will be executed first.'
            }
        }
        stage('Parallel Stage') {
            failFast true
            parallel {
                stage('Branch A') {
                    agent {
                        label "maven-skopeo-agent"
                    }
                    steps {
                        echo "On Branch A"
                        sleep 30
                    }
                }
                stage('Branch B') {
                    agent {
                        label "maven-skopeo-agent"
                    }
                    steps {
                        echo "On Branch B"
                        sleep 30
                    }
                }
                stage('Branch C') {
                    agent {
                        label "maven-skopeo-agent"
                    }
                    stages {
                        stage('Nested 1') {
                            steps {
                                echo "In stage Nested 1 within Branch C"
                                sleep 30
                            }
                        }
                        stage('Nested 2') {
                            steps {
                                echo "In stage Nested 2 within Branch C"
                                sleep 30
                            }
                        }
                    }
                }
            }
        }
    }
}
