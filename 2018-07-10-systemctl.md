

실행 중인 모든 서비스 보기

```
systemctl list-units --type=service
```

서비스 상태 확인

```
sudo systemctl status httpd.service
```

서비스 시작, 중지, 재시작

```
sudo systemctl start httpd.service
sudo systemctl stop httpd.service
sudo systemctl restart httpd.service
```

부팅 시 자동 시작/취소

```
systemctl enable httpd.service
systemctl disable httpd.service
```
