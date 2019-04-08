
Создать бэкап данных приложения:
docker exec -t gitlab_web_1 gitlab-rake gitlab:backup:create

cron:
0 23 * * * docker exec -t gitlab_web_1 gitlab-rake gitlab:backup:create

После этого файл бэкапа должен появиться в примонтированном к /opt/gitlab/ тому.

Создать бэкап конфигурации и секретных данных:
docker exec -t <your container name> /bin/sh -c 'umask 0077; tar cfz /secret/gitlab/backups/$(date "+etc-gitlab-\%s.tgz") -C / etc/gitlab'




gitlab_rails['smtp_enable'] = true
gitlab_rails['smtp_address'] = "smtp.gmail.com"
gitlab_rails['smtp_port'] = 587
gitlab_rails['smtp_user_name'] = "topazsender@gmail.com"
gitlab_rails['smtp_password'] = "WLgXFB7xFFC3Kh3"
gitlab_rails['smtp_domain'] = "smtp.gmail.com"
gitlab_rails['smtp_authentication'] = "login"
gitlab_rails['smtp_enable_starttls_auto'] = true
gitlab_rails['smtp_tls'] = false
gitlab_rails['smtp_openssl_verify_mode'] = 'peer' # Can be: 'none', 'peer', 'client_once', 'fail_if_no_peer_cert', see http://api.rubyonrails.org/classes/ActionMailer/Base.html

gitlab_rails['smtp_ca_path'] = "/etc/ssl/certs"
gitlab_rails['smtp_ca_file'] = "/etc/ssl/certs/ca-certificates.crt"
