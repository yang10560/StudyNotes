### SpringMVC 传参方式和返回类型

```java
package com.yang.controller;

import com.yang.common.Contacts;
import com.yang.dao.UserDao;
import com.yang.entity.User;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.*;
import org.springframework.web.servlet.ModelAndView;

import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import java.util.ArrayList;
import java.util.List;
import java.util.Map;

/**
 * @Author mryang
 * @Date 2020-09-25 14:55
 **/
@Controller
@RequestMapping("/user")
public class UserController {

    /**
     * 测试
     * @param modelAndView
     * @return
     */
    @RequestMapping("/hello")
    public ModelAndView hello(ModelAndView modelAndView){

        System.out.println("hello");
        modelAndView.setViewName("index");

        return  modelAndView;
    }


   /* @ResponseBody
    @RequestMapping(value = "/get1")
    public String get1() {
        System.out.println("get1......");
        return Contacts.SUCCESS;
    }*/


    /**
     * 传统传参方式
     */
    @RequestMapping("/test1")
    public String test1(HttpServletRequest httpServletRequest){
        String username = httpServletRequest.getParameter("username");
        String password = httpServletRequest.getParameter("password");
        User user = new User();
        user.setUsername(username);
        user.setPassword(password);
        System.out.println(user);
        return null;
    }

    /**
     *     简单类型参数和RequestParam注解
     * 　　如果请求参数和Controller方法的形参同名，可以直接接收
     * 　　如果请求参数和Controller方法的形参不同名，
     *    可以使用@RequestParam注解贴在形参前，设置对应的参数名称
     */
    @RequestMapping("/test2")
    public String test2(String username,String password){
        User user = new User();
        user.setUsername(username);
        user.setPassword(password);
        System.out.println(user);
        return null;
    }

    /**
     * 参数名不一样时。
     * @param un
     * @param pw
     * @return
     */
    @RequestMapping("/test3")
    public String test3(@RequestParam("username") String un, @RequestParam("password")String pw){

        User user = new User();
        user.setUsername(un);
        user.setPassword(pw);
        System.out.println(user);

        return null;
    }

    /**
     * 对象传参
     * 　　此时能够自动把参数封装到形参的对象上
     *
     * 　　注意：1、请求参数必须和对象的属性同名
     *
     * 　　　　    2、此时对象会直接放入request作用域中，名称为类型首字母小写
     *
     * 　　　　　3、@ModelAttribute设置请求参数绑定到对象中并传到视图页面，设置key值
     * @return ""
     */
    @RequestMapping("/test4")
    public ModelAndView test4(@ModelAttribute("u") User user){

        System.out.println(user);

        ModelAndView mv = new ModelAndView();
        mv.setViewName("test4");
        return mv;
    }

    /**
     * 当前台页面传来的参数是参数名相同，参数值不同的多个参数时，可以直接封装到方法的数组类型的形参中，也可以直接封装到对象的集合属性中。
     *
     * 　　比如批量删除时传来的参数。
     * /user/test5?ids=1,2,3
     * /user/test5?ids=1&ids=2&ids=3
     *
     * @param ids
     * @return
     */
    @RequestMapping("/test5")
    public String test5(String ids[]){
        for (String id : ids) {
            System.out.println(id);
        }
        return null;
    }

    /**
     * Restful是一种软件架构风格，严格上说是一种编码风格，其充分利用 HTTP 协议本身语义从而提供了一组设计原则和约束条件。
     *
     * 　　主要用于客户端和服务器交互类的软件，该风格设计的软件可以更简洁，更有层次，更易于实现缓存等机制。
     * 在后台，RequestMapping标签后，可以用{参数名}方式传参，同时需要在形参前加注解@PathVarible，假如前台的请求地址为localhost:8080/delete/3
     *
     * /user/test6/123
     *
     * @param id
     * @return
     */
    @RequestMapping("/test6/{id}")
    public String test6(@PathVariable("id")Integer id){

        System.out.println(id);

        return null;
    }


    /**
     * json对象
     * {
     *     "id":12,
     *     "username":"mryang",
     *     "password":"12345"
     * }
     * @param user
     * @return
     */
    @RequestMapping("/test7")
    public String test7(@RequestBody User user){

        System.out.println(user);

        return null;
    }
    /**
     * 传参json
     * @param user
     * @return
     */
    @RequestMapping("/test8")
    public String test8(@RequestBody String json){

        System.out.println(json);

        return null;
    }


    /**
     *
     * {}
     * class org.springframework.validation.support.BindingAwareModelMap
     * {}
     * class org.springframework.validation.support.BindingAwareModelMap
     *
     * @param map
     * @return
     */
    @RequestMapping("/test9")
    public String test9(Map<String,Object> map, Model model){

        System.out.println(map);
        System.out.println(map.getClass());
        System.out.println(model);
        System.out.println(model.getClass());
        return null;
    }

    /**
     * {username=mryang, password=123456}
     * class java.util.LinkedHashMap
     * {}
     * class org.springframework.validation.support.BindingAwareModelMap
     *
     * @param map
     * @return
     */
    @RequestMapping("/test10")
    public String test10(@RequestParam Map<String,Object> map,Model model){

        System.out.println(map);
        System.out.println(map.getClass());
        System.out.println(model);
        System.out.println(model.getClass());
        return null;
    }

    /**
     *
     * {id=12, username=mryang, password=12345}
     * class java.util.LinkedHashMap
     * {org.springframework.validation.BindingResult.map=org.springframework.validation.BeanPropertyBindingResult: 0 errors}
     * class org.springframework.validation.support.BindingAwareModelMap
     *
     * @param map
     * @param model
     * @return
     */
    @RequestMapping("/test11")
    public String test11(@RequestBody Map<String,Object> map,Model model){

        System.out.println(map);
        System.out.println(map.getClass());
        System.out.println(model);
        System.out.println(model.getClass());
        return null;
    }

    /*
     * 总结
     *
     * SpringMVC处理请求用Map类型接收参数时，如果参数无注解，则会传入BindingAwareModelMap类型，等价于Model、ModelMap参数；
     *
     * 参数添加@RequestParam注解时，会将参数包装称LinkedHashMap对象，参数的key为Map的key，参数值为Map的key，
     * 支持Get、Post方法（应该支持Put、Delete，没有测，俩方法与Post类似）；
     *
     * 添加@RequestBody注解时，接收Json类型数据，也会包装成LinkedHashMap对象，该注解不支持Get请求，Get请求没有请求体不能传Json。
     */

    /*
    ============================================================
     */

    /**
     * 返回json
     * @return
     */
    @GetMapping("/test12")
    @ResponseBody
    public List<User> test12(){

        List<User> users = new ArrayList<>();
        User user1 = new User();
        user1.setId(1l);
        user1.setUsername("aaa");
        user1.setPassword("1233");
        User user2 = new User();
        user2.setId(2l);
        user2.setUsername("bbbb");
        user2.setPassword("33333");
        users.add(user1);
        users.add(user2);
        return users;
    }

    /**
     * 返回string
     * @return
     */
    @RequestMapping("/test13")
    public String test13(){

        return "index";
    }

    /**
     * 返回mav
     * @param mv
     * @return
     */
    @RequestMapping("/test14")
    public ModelAndView test14(ModelAndView mv){
        mv.setViewName("index");
        return mv;
    }

    /**
     * 重定向
     * @return
     */
    @RequestMapping("/test15")
    public String test15(){

        return "redirect:/user/hello";
    }
    /**
     * 转发
     * @return
     */
    @RequestMapping("/test16")
    public String test16(){

        return "forward:/user/hello";
    }


}

```

