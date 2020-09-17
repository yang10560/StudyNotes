### **HQL语句形式**

**【1】select...**指定查询结果中的对象和属性，并指定以何种数据类型来返回，位置在HQL语句中排在最前面。

**【2】from...**指定HQL语句的查询目标，必须项（映射配置的持久化类及其属性）

**【3】where...**逻辑表达式，设置查询的条件，限制返回查询结果的范围

**【4】group by...**分组查询子句



### **使用select语句指定检索数据以哪种数据类型返回查询结果。**

**1、以Object[]形式返回选择的属性**

**2、以List集合形式返回选择的属性**

**3、以map形式返回选择的的属性**

**4、以自定义类型返回选择的属性**

**5、获取独特的结果——distinct关键字**

```java
    public void test3() {

        Query query = session.createQuery("select s.id,s.sname from Student s");
        //多个结果时对象数组(Object[])返回,当为一个时返回Object
        List<Object[]> list = query.list();
        for (Object[] objects : list) {
            System.out.println(objects[0]);
            System.out.println(objects[1]);
            System.out.println();
        }
        
    }
```

```java
@Test
    public void test4() {

        Query query = session.createQuery("select new list(s.id,s.sname) from Student s");
        //List返回
        List<List> list = query.list();
        for (List ls : list) {
            System.out.println(ls.get(0));
            System.out.println(ls.get(1));
            System.out.println();
        }
    }
```

``` java
    @Test
    public void test5() {
        Query query = session.createQuery("select new map(s.id,s.sname) from Student s");
        //MAP返回.key为所引值(字符串类型),value为查询索引对应的字段值。
        List<Map> maps = query.list();
        for (Map map : maps) {
            System.out.println(map.get("0"));
            System.out.println(map.get("1"));
            System.out.println();
        }
        System.out.println("=============");

        Query query1 = session.createQuery("select new map(s.id as id,s.sname as sname) from Student s");
        //MAP返回.key为别名
        List<Map> list = query1.list();
        for (Map map : maps) {
            System.out.println(map.get("id"));
            System.out.println(map.get("sname"));
            System.out.println();
        }

    }
```

``` java
 @Test
    public void test6() {
        Query query = session.createQuery("select new Student(s.id,s.sname) from Student s");
        //自己义类型，定义相应的构造器
        List<Student> students = query.list();
        for (Student student : students) {
            System.out.println(student);
        }
    }
```

### **where子句：逻辑表达式，设置查询的条件，来限制返回的查询结果，实际应用情况中，通常要求不是返回持久化类的所有查询结果，尤其是数据量非常庞大时。**

**1、比较运算**

**2、范围运算**

**3、字符串模式匹配**

**4.逻辑运算**

**5.集合运算**

---



### **比较运算：持久化类的属性与给定的查询条件进行比较。**

**1、比较运算符：=、<>、<、>、>=、<=。**

**2、null值判断————is [not] null，HQL中允许使用相等和不等进行null值判断，Hibernate框架会将x=null解析成x is null，x<>null解析成x is not null。**

```java
   @Test
    public void test6() {
        //Query query = session.createQuery("select s from Student s where s.sname=null");
        Query query = session.createQuery("select s from Student s where s.sname is null");
        List<Student> students = query.list();
        for (Student student : students) {
            System.out.println(student);
        }
    }
```

### **范围运算：判断属性值是否在给定的条件范围之内。**

**1、[not] in （列表）————进行的范围运算，in关键字后为候选值列表，该候选值列表可以明确指出也可以是子查询，当属性值在候选列表中存在返回true，否则返回false。**

**2、[not] between 值1 and 值2————指定一个值的范围，只要属性值在这个范围内，该运算就返回true值，否则返回false。**



### **字符串模式匹配：通过使用like关键字和通配符，对字符串类型的属性进行匹配运算（\**模糊查询\**）。**

**通配符：%、_。一个%形式可以匹配任意个字符，一个_形式匹配一个字符。**



### **逻辑运算符 1.and（逻辑与）、or（逻辑或） 2.not（逻辑非）**

```sql
e.g.  String hql="from Commodity c where c.price between 100 and 4000 and c.category like '%电脑%'";*
```



### **集合运算：HQL语句提供比较特殊的运算符，持久化映射中，存在一对多的映射配置，这里就可以使用集合运算符做相应的判定运算。**

**集合运算符：Hibernate框架会在hql解析过程中，解析成相应sql语句时**

**把empty——>exists运算**

**把member of——>in运算。**

**1、is [not] empty判断集合类型属性[不]为空，不包含任何元素。**

**2、member of判断实例是否属于该集合**

---



### **四则运算（+、-、\*、/）：对选择的属性做一些需要的运算。**

**1、HQL语句中也可以使用+、-、\*、/四则运算。**

**2、四则运算可以在where子句和select子句中使用**



### **查询单个对象**

**1、Query接口定义了uniqueResult方法，该方法强制返回结果只存在一个实例对象，而不再返回list集合形式的查询结果。**

**2、使用uniqueResult方法注意，通过where子句设置恰当的条件，保证符合查询条件的实例对象仅有一个，或者不存在，如果设置的查询条件不当，查询返回的实例对象多余一个，该方法就会抛出异常，终止运行。**

``` java
@Test
    public void test7() {
        Query<Student> query = session.createQuery("select s from Student s where s.id=1");
        Student s = query.getSingleResult();
        System.out.println(s);
    }
```

### **排序——order by子句**

**1、使用order by子句对查询结果排序，默认使用升序排序。**

**【a】升序排序——asc**

**【b】降序排序——desc**



### HQL中使用占位符

```java
 @Test
    public void test8() {
        //Query query = session.createQuery("select s from Student s where s.sname=null");
        Query query = session.createQuery("select s from Student s where s.id in(:sid)");
        query.setParameterList("sid",new Integer[]{1,32});
        List<Student> students = query.list();
        for (Student student : students) {
            System.out.println(student);
        }
    }
```



### **聚合函数**
sum    总计
avg    平均值
max    最大
min    最小
count  总数

### **HQL分页**

```java
 @Test
    public void test9() {
        Query query = session.createQuery("select s from Student s");
        query.setFirstResult(3);
        query.setMaxResults(3);
        List<Student> students = query.list();
        for (Student student : students) {
            System.out.println(student);
        }
    }
```

### **基类封装**

```java
package com.ht.five.Dao;
import java.util.Collection;
import java.util.List;
import java.util.Map;
import java.util.Map.Entry;
import java.util.Set;
import org.hibernate.Query;
import org.hibernate.Session;
import com.ht.five.Util.PageBean;

/**
 * 通用查询类
 * @author Administrator
 *
 */
public class BaseDao {
    /**
     * @param map 将要设置的阐述用Map的形式来传递
     * @param query 查询对象
     */
    public void setParam(Map<String, Object> map, Query query) {
        if(map != null && map.size() > 0) {
            Object value = null;
            Set<Entry<String, Object>> entries = map.entrySet();
            for (Entry<String, Object> entry : entries) {
                value = entry.getValue();
                //判断类型，根据类型来设置命名参数的值
                if(value instanceof Object[]) {
                    query.setParameterList(entry.getKey(), (Object[])value);
                }else if(value instanceof Collection) {
                    query.setParameterList(entry.getKey(), (Collection)value);
                }else {
                    query.setParameter(entry.getKey(), value);
                }
            }
        }
    }
    /**
     * 传入hql语句 ，返回该语句所查到的总行数
     * @param hql
     * @return
     */
    public String getCountHql(String hql) {
        /**
         * 下面这种做法的原因是请看这两条hql语句:
         * from Book 
         * select * from Book
         * 
         * 所有要想使这个方法同意就是将from这个位置做截断拼接
         */
        //获取到FROM的位置
        int index = hql.toUpperCase().indexOf("FROM");
        //直接从FROM截断，将select count(*) 拼接上就ok了
        return "select count(*)" + hql.substring(index);
    }

    
    /**
     *通用查询方法
     * @param session
     * @param map
     * @param hql
     * @param pageBean
     * @return
     */
    public List executeQuery(Session session, Map<String, Object> map, String hql, PageBean pageBean) {
        List list = null;
        if(pageBean != null && pageBean.isPagination()) {
            //获取该查询的总行数
            String countHql = getCountHql(hql);
            Query countQuery = session.createQuery(countHql);
            //给预定于的hql语句的命名参数赋值
            this.setParam(map, countQuery);
            //将总行数放入PageBean对象
            pageBean.setTotal(countQuery.getSingleResult().toString());
            
            Query query = session.createQuery(hql);
            //给预定于的hql语句的命名参数赋值
            this.setParam(map, query);
            //设置开始位置（下标从0开始）
            query.setFirstResult(pageBean.getStartIndex());
            //这是偏移量，就是一页展示几条数据
            query.setMaxResults(pageBean.getRows());
            list = query.list();
        }
        else {
            //如果不分页 直接查
            Query query = session.createQuery(hql);
            this.setParam(map, query);
            list = query.list();
        }
        return list;
    }
}
```

