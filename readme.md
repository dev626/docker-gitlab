������� ����� ������ ����������:
docker exec -t gitlab_web_1 gitlab-rake gitlab:backup:create

cron:
0 23 * * * docker exec -t gitlab_web_1 gitlab-rake gitlab:backup:create

����� ����� ���� ������ ������ ��������� � ���������������� � /opt/gitlab/ ����.

������� ����� ������������ � ��������� ������:
docker exec -t <your container name> /bin/sh -c 'umask 0077; tar cfz /secret/gitlab/backups/$(date "+etc-gitlab-\%s.tgz") -C / etc/gitlab'