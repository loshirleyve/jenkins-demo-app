pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
    }

    stages {

        stage('📦 安装依赖') {
            steps {
                echo 'Installing dependencies...'
                sh 'npm install'
            }
        }

        stage('🔍 代码检查') {
            steps {
                echo 'Running lint...'
                sh 'npm run lint'
            }
        }

        stage('🧪 单元测试') {
            steps {
                echo 'Running tests...'
                sh 'npm run test'
            }
        }

        stage('🛠️ 构建') {
            steps {
                echo 'Building project...'
                sh 'npm run build'
            }
            post {
                success {
                    // 构建成功，把产物归档
                    archiveArtifacts artifacts: 'dist/**', fingerprint: true
                }
            }
        }

    }

    post {
        success {
            echo '🎉 所有阶段通过！'
        }
        failure {
            echo '💥 流水线失败，请检查日志'
        }
    }
}