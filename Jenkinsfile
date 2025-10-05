pipeline {
    agent any

    parameters {
        string(name: 'DB_NUMBER', defaultValue: 'all', description: 'Номер бази даних для очищення або "all" для очищення всіх баз даних')
    }

    stages {
        stage('Initialization') {
            steps {
                echo "Ініціалізація параметрів. Параметр DB_NUMBER=${DB_NUMBER}"
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                echo "Запуск плейбука для очищення Redis..."
                sh """
                ansible-playbook /home/sukhovoy/ansible/flush_redis.yml --extra-vars "redis_db=${DB_NUMBER}"
                """
            }
        }

        stage('Finalize') {
            steps {
                echo "Очищення Redis завершено для DB_NUMBER=${DB_NUMBER}"
            }
        }
    }
}
