pipeline {
    agent { label "Python" }
    stages {
        stage('BlackDuck') {
            steps {
                sh """virtualenv env
                      . env/bin/activate
                      pip install -r requirements.txt
                      # If locally run 'python manage.py runserver' => 'Hello, world' appears in htp://127.0.0.1:8000
                """
                hub_detect '--blackduck.hub.trust.cert="true" --detect.pip.requirements.path="requirements.txt" --detect.risk.report.pdf="true"'// --detect.python.path="/usr/bin/python"'
                archiveArtifacts '*.pdf'
            }
        }
    }
}
