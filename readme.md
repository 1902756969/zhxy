# 硅谷智慧校园项目(包含sql)

##### 技术栈：mysql+Springboot+MP+jwt+SpringMVC+thymeleaf



## Pojo类

```java
@Data
@AllArgsConstructor
@NoArgsConstructor
@TableName("tb_admin")
public class Admin {
    @TableId(value = "id",type = IdType.AUTO)
    private Integer id;
    private String name;
    private char gender;
    private String password;
    private String email;
    private String telephone;
    private String address;
    private String portraitPath;// 头像的图片路径
}
```

```java
/**
 * @project: sms
 * @description: 班级信息
 */
@Data
@TableName("tb_clazz")
public class Clazz {
    //班级信息
    @TableId(value = "id",type = IdType.AUTO)
    private Integer id;             //班级Id
    private String name;            //班级名称
    private String number;          //班级人数
    private String introducation;   //班级介绍
    //班主任信息
    private String headmaster;      //班主任姓名
    private String telephone;       //班主任电话
    private String email;           //班主任邮箱
    //所属年级
    private String gradeName;      //班级所属年级


}
```

```java
/**
 * @project: sms
 * @description: 年级及年级主任信息
 */
@Data
@TableName("tb_grade")
public class Grade {

    //年级信息
    @TableId(value = "id",type = IdType.AUTO)
    private Integer id;             //年级ID
    private String name;            //年级名称
    private String introducation;   //年级介绍
    //年级主任信息
    private String manager;         //年级主任姓名
    private String email;           //年级主任邮箱
    private String telephone;       //年级主任电话

}
```

```java
/**
 * @project: ssm_sms
 * @description: 用户登录表单信息
 */
@Data
public class LoginForm {

    private String username;
    private String password;
    private String verifiCode;
    private Integer userType;

}
```

```java
/**
 * @project: sms
 * @description: 学生信息
 */
@Data
@TableName("tb_student")
public class Student {

    @TableId(value = "id",type = IdType.AUTO)
    private Integer id;
    private String sno;
    private String name;
    private char gender = '男';//default
    private String password;
    private String email;
    private String telephone;
    private String address;
    private String introducation;
    private String portraitPath;//存储头像的项目路径
    private String clazzName;//班级名称

}
```

```java
/**
 * @project: sms
 * @description: 教师信息
 */
@Data
@TableName("tb_teacher")
public class Teacher {

    @TableId(value = "id",type = IdType.AUTO)
    private Integer id;
    private String tno;
    private String name;
    private char gender;
    private String password;
    private String email;
    private String telephone;
    private String address;
    private String clazzName;
    private String portraitPath;//存储头像的项目路径

//    @TableLogic
//    private Integer isDeleted;
}
```

## MD5加密

```java
public final class MD5 {

    public static String encrypt(String strSrc) {
        try {
            char hexChars[] = { '0', '1', '2', '3', '4', '5', '6', '7', '8',
                    '9', 'a', 'b', 'c', 'd', 'e', 'f' };
            byte[] bytes = strSrc.getBytes();
            MessageDigest md = MessageDigest.getInstance("MD5");
            md.update(bytes);
            bytes = md.digest();
            int j = bytes.length;
            char[] chars = new char[j * 2];
            int k = 0;
            for (int i = 0; i < bytes.length; i++) {
                byte b = bytes[i];
                chars[k++] = hexChars[b >>> 4 & 0xf];
                chars[k++] = hexChars[b & 0xf];
            }
            return new String(chars);
        } catch (NoSuchAlgorithmException e) {
            e.printStackTrace();
            throw new RuntimeException("MD5加密出错！！+" + e);
        }
    }


}
```

### 界面展示

![image](https://cdn.staticaly.com/gh/1902756969/picgo_imgs@master/image.2uk7wtmg4o60.webp)

![image](https://cdn.staticaly.com/gh/1902756969/picgo_imgs@master/image.x3j26avocao.webp)



## 学生登录后

高启强 123456

![image](https://cdn.staticaly.com/gh/1902756969/picgo_imgs@master/image.70domjq8gzc0.webp)



## 管理员登录后

admin admin

![image](https://cdn.staticaly.com/gh/1902756969/picgo_imgs@master/image.wlwk3nk4zhc.webp)



## 教师登录后

大圣  123456

![image](https://cdn.staticaly.com/gh/1902756969/picgo_imgs@master/image.lbch3ikhjto.webp)