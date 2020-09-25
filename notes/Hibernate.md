### Spring Data JPA

 

- pom.xml

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>5.1.48</version>
        <scope>runtime</scope>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
        <version>2.2.1.RELEASE</version>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
        <exclusions>
            <exclusion>
                <groupId>org.junit.vintage</groupId>
                <artifactId>junit-vintage-engine</artifactId>
            </exclusion>
        </exclusions>
    </dependency>
</dependencies>
```

- application.yml

  ```yaml
  spring:
    datasource:
      username: root
      password: admin
      url: jdbc:mysql:///test2
      driver-class-name: com.mysql.jdbc.Driver
      type: com.zaxxer.hikari.HikariDataSource
    jpa:
      open-in-view: false
      hibernate:
        ddl-auto: none
        use-new-id-generator-mappings: false
      show-sql: true
  ```

- 数据结构

```mysql
/*
Navicat MySQL Data Transfer

Source Server         : mysql
Source Server Version : 50027
Source Host           : localhost:3306
Source Database       : test2

Target Server Type    : MYSQL
Target Server Version : 50027
File Encoding         : 65001

Date: 2020-09-22 10:30:16
*/

SET FOREIGN_KEY_CHECKS=0;
-- ----------------------------
-- Table structure for t_class
-- ----------------------------
DROP TABLE IF EXISTS `t_class`;
CREATE TABLE `t_class` (
  `id` int(11) NOT NULL auto_increment,
  `className` varchar(255) default NULL,
  PRIMARY KEY  (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of t_class
-- ----------------------------
INSERT INTO `t_class` VALUES ('1', '一班');
INSERT INTO `t_class` VALUES ('2', '二班');

-- ----------------------------
-- Table structure for t_course
-- ----------------------------
DROP TABLE IF EXISTS `t_course`;
CREATE TABLE `t_course` (
  `id` int(11) NOT NULL auto_increment,
  `cname` varchar(255) default NULL,
  PRIMARY KEY  (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of t_course
-- ----------------------------
INSERT INTO `t_course` VALUES ('1', '化学');
INSERT INTO `t_course` VALUES ('2', '数学');
INSERT INTO `t_course` VALUES ('3', '生物');
INSERT INTO `t_course` VALUES ('4', '物理');

-- ----------------------------
-- Table structure for t_user
-- ----------------------------
DROP TABLE IF EXISTS `t_user`;
CREATE TABLE `t_user` (
  `id` int(11) NOT NULL auto_increment,
  `username` varchar(255) default NULL,
  `password` varchar(255) default NULL,
  `c_id` int(11) default NULL COMMENT '班级',
  PRIMARY KEY  (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

-- ----------------------------
-- Records of t_user
-- ----------------------------
INSERT INTO `t_user` VALUES ('1', 'admin3', '88888', '1');
INSERT INTO `t_user` VALUES ('2', 'makrs', '32232', '2');
INSERT INTO `t_user` VALUES ('3', 'jackuy', '565656', '2');

-- ----------------------------
-- Table structure for user_course
-- ----------------------------
DROP TABLE IF EXISTS `user_course`;
CREATE TABLE `user_course` (
  `id` int(11) NOT NULL auto_increment,
  `uid` int(11) default NULL,
  `cid` int(11) default NULL,
  PRIMARY KEY  (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of user_course
-- ----------------------------
INSERT INTO `user_course` VALUES ('1', '1', '1');
INSERT INTO `user_course` VALUES ('2', '1', '2');
INSERT INTO `user_course` VALUES ('3', '1', '4');
INSERT INTO `user_course` VALUES ('4', '2', '2');
INSERT INTO `user_course` VALUES ('5', '2', '3');
INSERT INTO `user_course` VALUES ('6', '3', '1');
INSERT INTO `user_course` VALUES ('7', '3', '4');

```

- Dao

  ```java
  public interface ClazzDao extends JpaRepository<Clazz,Long>, JpaSpecificationExecutor<Clazz> {
  
  }
  public interface CourseDao extends JpaRepository<Course,Long> , JpaSpecificationExecutor<Course> {
      
  }
  public interface UserDao extends JpaRepository<User,Long> , JpaSpecificationExecutor<User> {
  
  }
  ```

  - 实体类

    User

    ``` java
    @Entity
    @Table(name = "t_user")
    public class User implements Serializable {
    
    
        //多对一 
        @ManyToOne()
        @JoinColumn(name = "c_id",referencedColumnName = "id")//user表外键-Class表主键
        private Clazz clazz;
    
        @Id()
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        private Long id;
    
        @Column(name = "username")
        private String username;
    
        @Column(name = "password")
        private String passsword;
    
    
        //多对多
        @ManyToMany(targetEntity = Course.class,fetch = FetchType.EAGER)
        @JoinTable(name = "user_course",joinColumns = @JoinColumn(name = "uid"),
                inverseJoinColumns = @JoinColumn(name = "cid"))//中间表
        private List<Course> courses;
        
        //getter setter   
    }
    
    ```

    Class

    ``` java
    @Entity
    @Table(name = "t_class")
    public class Clazz implements Serializable {
    
    
        //一对多   mappedBy User表的属性名
        @OneToMany(mappedBy = "clazz",fetch = FetchType.EAGER)
        private List<User> users;
    
        @Id()
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        private Long id;
    
        @Column(name = "classname")
        private String className;
        
        //getter setter
    }
    ```

    Course

    ``` java
    @Entity
    @Table(name = "t_course")
    public class Course implements Serializable {
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        private Long id;
    
        @Column(name = "cname")
        private String name;
    
    
        //mapperBy user表的属性名
        @ManyToMany(targetEntity = User.class,mappedBy = "courses",fetch = FetchType.EAGER)
        private List<User> users;
     
        //getter setter
    }
    ```

    - 测试

      ```java
      @Test
          void contextLoads() {
              //多对一
              List<User> all = userDao.findAll();
              for (User user : all) {
                  System.out.println(user);
                  System.out.println(user.getClazz());
              }
          }
          /**
      User{id=1, username='admin3', passsword='88888'}
      Clazz{id=1, className='一班'}
      User{id=2, username='makrs', passsword='32232'}
      Clazz{id=2, className='二班'}
      User{id=3, username='jackuy', passsword='565656'}
      Clazz{id=2, className='二班'}
      **/
         @Test
          void t1() {
              //一对多
              List<Clazz> all = clazzDao.findAll();
              for (Clazz clazz : all) {
                  System.out.println(clazz);
                  System.out.println(clazz.getUsers());
              }
      
          }
      /**
      Clazz{id=1, className='一班'}
      [User{id=1, username='admin3', passsword='88888'}]
      Clazz{id=2, className='二班'}
      [User{id=2, username='makrs', passsword='32232'}, User{id=3, username='jackuy', passsword='565656'}]
      **/
       @Test
          void t2() {
              //多对多
              List<Course> courses= courseDao.findAll();
              for (Course cours : courses) {
                  System.out.println(cours);
                  List<User> users = cours.getUsers();
                  for (User user : users) {
                      System.out.println(user);
                  }
                  System.out.println("============================");
              }
      
              System.out.println("===============分割线============");
      
              //多对多
              List<User> users= userDao.findAll();
              for (User user : users) {
                  System.out.println(user);
                  List<Course> courses1 = user.getCourses();
                  for (Course course : courses1) {
                      System.out.println(course);
                  }
                  System.out.println("============================");
              }
          }
      /**
      Course{id=1, name='化学'}
      User{id=1, username='admin3', passsword='88888'}
      User{id=3, username='jackuy', passsword='565656'}
      ============================
      Course{id=2, name='数学'}
      User{id=1, username='admin3', passsword='88888'}
      User{id=2, username='makrs', passsword='32232'}
      ============================
      Course{id=3, name='生物'}
      User{id=2, username='makrs', passsword='32232'}
      ============================
      Course{id=4, name='物理'}
      User{id=1, username='admin3', passsword='88888'}
      User{id=3, username='jackuy', passsword='565656'}
      ============================
      ===============分割线============
      
      User{id=1, username='admin3', passsword='88888'}
      Course{id=1, name='化学'}
      Course{id=2, name='数学'}
      Course{id=4, name='物理'}
      ============================
      User{id=2, username='makrs', passsword='32232'}
      Course{id=2, name='数学'}
      Course{id=3, name='生物'}
      ============================
      User{id=3, username='jackuy', passsword='565656'}
      Course{id=1, name='化学'}
      Course{id=4, name='物理'}
      ============================
      
      **/
      
      
      ```

      

