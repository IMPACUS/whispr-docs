## DEV 서버 배포 정보

### EC2, RDS

- EC2
  - host: ec2-43-202-168-134.ap-northeast-2.compute.amazonaws.com
  - pem key: [pem key](https://github.com/IMPACUS/whispr-docs/blob/master/be/assets/ec2-dev-whispr.pem)
- RDS
  - host: rds-dev-whispr.c6unqkaeefhz.ap-northeast-2.rds.amazonaws.com
  - user: root
  - password: Qwer12#$

### Github secret variables


| key             | value                                                   |
| :-------------- | ------------------------------------------------------- |
| DOCKER_USERNAME | lchy0413                                                |
| DOCKER_PASSWORD | a4n4g4e4l4                                              |
| DOCKER_REPO     | lchy0413/impacus-dev                                    |
| AWS_HOST        | ec2-43-202-168-134.ap-northeast-2.compute.amazonaws.com |
| AWS_KEY         | ec2 pem key 내용                                        |
