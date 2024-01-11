
### context-datasource.xml
```
<bean id="dataSource" class="org.apache.commons.dbcp.BasicDataSource" destroy-method="close">
  <property name="driverClassName" value="com.mysql.jdbc.Driver"/>
  <property name="url" value="jdbc:mysql://192.168.114.128:3306/jd" />
  <property name="username" value="jd2"/>
  <property name="password" value="1Q2W3e4r!!"/>
</bean>
```

```
org.apache.commons.dbcp.SQLNestedException: Cannot create PoolableConnectionFactory (The server time zone value 'KST' is unrecognized or represents more than one time zone. You must configure either the server or JDBC driver (via the serverTimezone configuration property) to use a more specifc time zone value if you want to utilize time zone support.)
```

위와 같은 에러가 난다면

property name="url"에 다음 내용을 추가한다
```
?useUnicode=true&amp;useJDBCCompliantTimezoneShift=true&amp;useLegacyDatetimeCode=false&amp;serverTimezone=UTC

ex)
<property name="url" value="jdbc:mysql://192.168.114.128:3306/jd?useUnicode=true&amp;useJDBCCompliantTimezoneShift=true&amp;useLegacyDatetimeCode=false&amp;serverTimezone=UTC" />
```

