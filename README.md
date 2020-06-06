# Restaurant voting RESTfull application

Используемые технологии:
<li>SpringBoot 2</li>
<li>Spring MVC</li>
<li>Spring Data JPA</li>
<li>Spring Security</li>
<li>Hibernate</li>
<li>Jackson</li>
<li>Tomcat (embedded)</li>
<li>H2</li>
<li>JUnit</li>
<li>Maven</li><br>

2 типа пользователей: USER, ADMIN

Админ: Редактирует рестораны, меню. Обновляет меню каждый день.

Пользователь: Голосует за ресторан в котором хотел бы пообедать. Учитывается только один голос в день для пользователя.
Пользователь может изменить голос только до 11:00.

---

## Rest API
### User
#### get all restaurants with menu today
`curl -s http://localhost:8080/rest/user/restaurants --user user1@mail.com:password1`
#### get restaurant id=100005 with menu today
`curl -s http://localhost:8080/rest/user/restaurants/100005 --user user1@mail.com:password1`
#### create vote
`curl -s -X POST -H 'Content-Type:application/json;charset=UTF-8' http://localhost:8080/rest/user/restaurants/100005/votes --user user2@mail.com:password2`
#### update vote
`curl -s -X PUT -H 'Content-Type:application/json;charset=UTF-8' http://localhost:8080/rest/user/restaurants/100005/votes --user user1@mail.com:password1`
#### get vote history
`curl -s http://localhost:8080/rest/user/votes/history --user user1@mail.com:password1`
#### get vote history between dates
`curl -s 'http://localhost:8080/rest/user/votes/history?startDate=2020-01-01&endDate=2020-04-30' --user user1@mail.com:password1`
#### register Users
`curl -s -i -X POST -d '{"name":"New User","email":"test@mail.ru","password":"test-password"}' -H 'Content-Type:application/json;charset=UTF-8' http://localhost:8080/rest/user/register`

### Admin 
#### get all restaurants
`curl -s http://localhost:8080/rest/admin/restaurants --user admin@mail.com:admin`
#### get restaurant with id=100003
`curl -s http://localhost:8080/rest/admin/restaurants/100003 --user admin@mail.com:admin`
#### create restaurant
`curl -s -X POST -d '{"name":"Restaurant"}' -H 'Content-Type:application/json;charset=UTF-8' http://localhost:8080/rest/admin/restaurants --user admin@mail.com:admin`
#### update restaurant with id=100003
`curl -s -X PUT -d '{"id":100003, "name":"Rest"}' -H 'Content-Type:application/json;charset=UTF-8' http://localhost:8080/rest/admin/restaurants/100003 --user admin@mail.com:admin`
#### delete restaurant with id=100003
`curl -s -X DELETE http://localhost:8080/rest/admin/restaurants/100003 --user admin@mail.com:admin`
#### get all dishes by restaurant id=100004
`curl -s http://localhost:8080/rest/admin/restaurants/100004/dishes --user admin@mail.com:admin`
#### get dish by id=100010
`curl -s http://localhost:8080/rest/admin/dishes/100010 --user admin@mail.com:admin`
#### create dish
`curl -s -X POST -d '{"name":"Kefir", "date":"2020-05-05", "price":250}' -H 'Content-Type:application/json;charset=UTF-8' http://localhost:8080/rest/admin/restaurants/100004/dishes --user admin@mail.com:admin`
#### update dish with id=100010
`curl -s -X PUT -d '{"id":100010, "name":"Tvorog", "date":"2020-05-05", "price":250}' -H 'Content-Type:application/json;charset=UTF-8' http://localhost:8080/rest/admin/restaurants/100004/dishes/100010 --user admin@mail.com:admin`
#### delete dish with id=100010
`curl -s -X DELETE http://localhost:8080/rest/admin/dishes/100010 --user admin@mail.com:admin`
#### get votes by restaurant with id=100004
`curl -s http://localhost:8080/rest/admin/restaurant/100004/votes --user admin@mail.com:admin`
#### get votes today
`curl -s http://localhost:8080/rest/admin/votes/history --user admin@mail.com:admin`
#### get votes between dates
`curl -s 'http://localhost:8080/rest/admin/votes/history?startDate=2020-04-01&endDate=2020-05-05' --user admin@mail.com:admin`