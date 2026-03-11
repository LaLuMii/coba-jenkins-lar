node {
    // Mengambil kode dari Source Control Management
    checkout scm

    // Tahap Build
    stage("Build") {
        // Menggunakan image resmi dengan versi spesifik (PHP 8.3 + Composer 2.7.1)
        docker.image('composer:2.7.1').inside('-u root') {
            // Menghapus lock file agar instalasi bersih (opsional)
            sh 'rm -f composer.lock'
            
            // Menggunakan flag --no-interaction agar tidak berhenti menunggu input
            sh 'composer install --no-interaction --prefer-dist --optimize-autoloader'
        }
    }

    // Tahap Testing
    stage("Testing") {
        // Menggunakan Ubuntu dengan tag versi stabil (22.04 LTS)
        docker.image('ubuntu:22.04').inside('-u root') {
            sh 'echo "Menjalankan unit testing pada lingkungan terkontrol"'
            // Tambahkan perintah test Anda di sini, misalnya:
            // sh './vendor/bin/phpunit'
        }
    }
}