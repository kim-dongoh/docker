# .ldif 파일 적용
> https://github.com/osixia/docker-openldap

컨테이너 내 아래 경로에 있는 `.ldif` 파일의 경우 컨테이너 생성 시 자동으로 적용
* `/container/service/slapd/assets/config/bootstrap/ldif/custom`

`.ldif` 파일 내 `DN`의 경우, `{{ LDAP_BASE_DN }}` 으로 기입 가능


# docker volume mount 문제
> https://github.com/osixia/docker-openldap#fix-docker-mounted-file-problems

## docker-compose.yml
```
command: "--copy-service"
```
`--copy-service` 명령어 추가


## docker CLI
```
docker run \
	--volume ./ldap_users:/container/service/slapd/assets/config/bootstrap/ldif/custom \
	osixia/openldap:1.5.0 --copy-service
```
`--copy-service` 옵션 추가
