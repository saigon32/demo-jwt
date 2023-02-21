# demo-jwt
Demo de un API REST que utiliza JWT

# 1) Se lanza una petición de login, en esta primera petición se observa que devuelve el jwt en la cabecera, como en el siguiente
# ejemplo, de ahora en adelante se usara: Authorization: Bearer + <jwt-token>, en la cabecera de las siguientes peticiones:
# Authorization: Bearer  eyJhbGciOiJIUzUxMiJ9.eyJpYXQiOjE2NzcwMTQwNTAsImlzcyI6Imh0dHBzOi8vd3d3LmF1dGVudGlhLmNvbS8iLCJzdWIiOiJhZG1pbiIsImV4cCI6MTY3Nzg3ODA1MH0.2pfffX0gYB9rz5A1x4rfFtfho0VagX76VQEeZhCKhvrlCFXs_wLe-qyW3gmQzYXrwYs1iQJ5lorbpoPg9uqcGA
$ curl -i -H "Content-Type: application/json" -X POST -d '{ "username": "admin", "password": "password"}' http://localhost:8080/login
% Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
Dload  Upload   Total   Spent    Left  Speed
100    46    0     0  100    46      0    429 --:--:-- --:--:-- --:--:--   433HTTP/1.1 200
X-Content-Type-Options: nosniff
X-XSS-Protection: 1; mode=block
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Pragma: no-cache
Expires: 0
X-Frame-Options: DENY
Authorization: Bearer  eyJhbGciOiJIUzUxMiJ9.eyJpYXQiOjE2NzcwMTQwNTAsImlzcyI6Imh0dHBzOi8vd3d3LmF1dGVudGlhLmNvbS8iLCJzdWIiOiJhZG1pbiIsImV4cCI6MTY3Nzg3ODA1MH0.2pfffX0gYB9rz5A1x4rfFtfho0VagX76VQEeZhCKhvrlCFXs_wLe-qyW3gmQzYXrwYs1iQJ5lorbpoPg9uqcGA
Content-Length: 0
Date: Tue, 21 Feb 2023 21:14:10 GMT

# 2) Recuperamos los usuarios dados de alta, usando el header en la cabecera, Authorization: Bearer + <jwt-token>
$ curl -H "Authorization: Bearer  eyJhbGciOiJIUzUxMiJ9.eyJpYXQiOjE2NzcwMTYwNjcsImlzcyI6Imh0dHBzOi8vd3d3LmF1dGVudGlhLmNvbS8iLCJzdWIiOiJhZG1pbiIsImV4cCI6MTY3Nzg4MDA2N30.OWuhAhbbVCDM8F6UZ6xd6vwx8uEfBkQEAu3andOY2v_fjrANSrHa--iF1dMHWm6MLxjeCN2qb964Chl22xBsCg" http://localhost:8080/users/
% Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
Dload  Upload   Total   Spent    Left  Speed
100   624    0   624    0     0  27130      0 --:--:-- --:--:-- --:--:-- 27130
[{"id":1,"username":"admin","password":"$2a$10$XURPShQNCsLjp1ESc2laoObo9QZDhxz73hJPaEv7/cBha4pk0AgP."},
 {"id":2,"username":"daenerys","password":"$2a$10$nVnT9Y7.my.KvCPARqH3KOunil8.IAx6DG8ze1f1X.OTh9.dShUeu"},
 {"id":3,"username":"daenerys","password":"$2a$10$COh9uR9qCp6cOvyoLDlmkuk.JPrj4Q6e0ZVojnuKxNoPoAp98UarK"},
 {"id":4,"username":"daenerys","password":"$2a$10$96M7g1lfM5q2Q0a3CSZnb.VN69MAtbih0B93lVA9cnjlEWYRr55Au"},
 {"id":5,"username":"daenerys","password":"$2a$10$Gmx8hp9gTYTp2F0MWaVuyO/AB5Z1akUkMCis/nMTT6dkxNGrMKK9K"},
 {"id":6,"username":"juan","password":"$2a$10$gYjR5vsLHFph5sSOJzc14OmQYszHB8qapWepSjD7/jASmawVWmkIK"}]


# 3) Damos de alta un nuevo usuario, usando el header en la cabecera, Authorization: Bearer + <jwt-token>, 
# inserta un usuario mas a la tabla de login, si ejecutamos el paso 2, veremos el nuevo usuario creado
$ curl -i -H 'Content-Type: application/json' -H 'Authorization: Bearer eyJhbGciOiJIUzUxMiJ9.eyJpYXQiOjE2NzcwMTY2NDAsImlzcyI6Imh0dHBzOi8vd3d3LmF1dGVudGlhLmNvbS8iLCJzdWIiOiJhZG1pbiIsImV4cCI6MTY3Nzg4MDY0MH0.ILniV0IggoaU-XpW2QpV4K7JqZxOsKF89ce7WfJwxOBj3Fd06moS_QfSC4bX5gonXaWCSI2aZzvKoQfRjBA5cA' -X POST -d '{ "username": "juan", "password": "valdez"}' http://localhost:8080/users/
% Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
Dload  Upload   Total   Spent    Left  Speed
100    43    0     0  100    43      0    417 --:--:-- --:--:-- --:--:--   421HTTP/1.1 200
X-Content-Type-Options: nosniff
X-XSS-Protection: 1; mode=block
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Pragma: no-cache
Expires: 0
X-Frame-Options: DENY
Content-Length: 0
Date: Tue, 21 Feb 2023 22:05:01 GMT

manuel de referencia: 
https://www.adictosaltrabajo.com/2017/09/25/securizar-un-api-rest-utilizando-json-web-tokens/

JWT online token:
https://jwt.io/









