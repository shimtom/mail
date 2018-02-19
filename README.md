# Mail Server

## アカウント作成
```bash
$ mkdir -p config
$ touch config/postfix-accounts.cf
$ docker run --rm \
  -e MAIL_USER=user1@domain.tld \
  -e MAIL_PASS=mypassword \
  -ti tvial/docker-mailserver:latest \
  /bin/sh -c 'echo "$MAIL_USER|$(doveadm pw -s SHA512-CRYPT -u $MAIL_USER -p $MAIL_PASS)"' >> config/postfix-accounts.cf
```

## 参考
* https://github.com/tomav/docker-mailserver
