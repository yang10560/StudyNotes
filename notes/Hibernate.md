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


​    
### 深入理解Hibernate三种状态



状态之间如何转换

![](\pics\hbn.png)

```java
1. Save和Update：save的时候是将自由态的对象持久化到数据库中，而update的时候一般是将游离态的对象持久化到数据库中去。

2. update、saveOrUpdate、merge：saveOrUpdate的作用是当Session中存在要操作的对象的时候，抛出异常信息，当不存在的时候，如果这个对象没有持久化标识属性，那么将这个对象save，如果这个对象有持久化标识属性的话，那么直接update就可以了。对于单纯的update来说，程序会在一个Session中加载对象，然后将这个对象关闭，然后这个对象发生变化之后，再update的时候就会打开另一个Session将对象持久化到数据库中去。merge的话是当Session中存在要操作的对象的时候，不会抛出异常而是直接将这个对象的数据拷贝到Session中持久态的对象中去，这样对象还是维持着原来的状态。

3.persist和save：都是用来保存临时对象到数据库的，但是persist并不保证对象的主键立即被创建好，有可能推迟到flush的时候。但是save的时候会立即创建好的，所以save的时候一般可以通过对象拿到主键值。

4. flush和update：update的时候对象多是游离态的对象，也就是说数据库中已经存在了，但是并不在Session中的对象通过update会更新到数据库当中去。而flush是将本来持久态的数据更新到数据库中去。

5. lock是将一个没有更改过的托管的对象转为持久态的对象，但是他不能针对那些delete后的托管的对象。

User user = new User();
user.setName("wy");
//目前还是一个临时对象
Session session = sessionFactory.openSession();
Tansaction tx = session.beginTansaction();
//目前还是一个临时对象
session.save(user);
//user处于持久态了
tx.commit();
session.close();// 游离态了
```

``` java
问题在哪里
      Hibernate分为三种基本的状态：游离态、自由态（临时状态）、持久态。
      持久化状态：与session关联并且和在数据库有数据，已经持久化了并且在数据库的缓存当中了。
      我这里的这个对象应该是持久化状态的对象然后我直接构造了一个user对象的set集合，同时对这个对象进行set操作，那么缓存Session中的数据发生改变，那么接着数据库也会跟着进行相应的改变。所以就执行了update的更新操作。


怎么解决
     其他两种状态：
     1. 临时状态：就是直接new出来的对象，既没有持久化到数据库中去，也没有在session当中。
     2. 游离状态：在Session中没有了，但是已经持久化到了数据库当中。
     
     那么这个地方怎么解决呢？
     1.如果这个对象（例子中的company）本身不需要用的话,可以直接new一个Company的对象出来然后再setUsers这个时候因为不是Session中的数据，那么不会因为对象的属性发生改变而同步到数据库中去。
     2. 如果这个对象（例子中的company）要用的到，那么，在set之前可以先将其转为游离态，这样的话会用到session的几个方法：close、clear、evict。
     close方法：关闭session这样这个对象肯定是游离态了，因为session已经关闭了，但是往往我们实际的开发过程中，session在后面是要用的到的，所以这个方法可行，但是不一定用得上，分清具体的情况。
     clear方法：将session中的所有的对象全部清除出缓存，这个方式有点劳师动众，不过session清除了全部的对象之后自然就会变为游离态了，这样做不是很好吧我感觉。
     evict方法：将某一个对象清除出缓存session，这个方法是很好的实现方式，推荐使用。调用的时候是这样的，session.evict(Object obj);这样就可以了。

```

