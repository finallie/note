# 使用JUnit5、Mockito、SpringBootTest写单元测试

>## 1.demo依赖版本

### SpringBoot版本 2.2.1.RELEASE

SpringBootTest自带JUnit5、Mockito相关依赖

```xml
    <dependency>
      <groupId>org.mockito</groupId>
      <artifactId>mockito-junit-jupiter</artifactId>
      <version>3.1.0</version>
      <scope>compile</scope>
    </dependency>
    <dependency>
      <groupId>org.junit.jupiter</groupId>
      <artifactId>junit-jupiter</artifactId>
      <version>5.5.2</version>
      <scope>compile</scope>
    </dependency>
```

### maven-surefire-plugin

执行junit5单元测试需要此插件版本在2.22.2以上

```xml
    <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-surefire-plugin</artifactId>
        <version>2.22.2</version>
        <configuration>
            <forkCount>1</forkCount>
            <runOrder>random</runOrder>
            <testFailureIgnore>true</testFailureIgnore>
        </configuration>
    </plugin>
```

>## 2.JUnit5与JUnit4区别

JUnit5与JUnit4依赖包名不同，一些常用的注解名字不同

相关文档：[https://junit.org/junit5/docs/current/user-guide/#overview]

 ||JUnit5 | JUnit4
|---| ----------- | ----------- |
|@Test包名|org.junit.jupiter.api|org.junit
|Assertions包名|org.junit.jupiter.api.Assertions.*|org.junit.Assert.*
||@ExtendWith|@RunWith
||@Disabled |@Before
||@BeforeEach  |@Ignore

>## 3.Mockito

### 相关文档

- [https://javadoc.io/doc/org.mockito/mockito-core/latest/org/mockito/Mockito.html]

- [https://site.mockito.org/]

>### demo

```java
//待测试类
@Service
public class DcSysUserServiceImpl extends ServiceImpl<DcSysUserMapper, DcSysUser> implements DcSysUserService, IServiceHandle<DcSysUser> {

    @Autowired
    DcSysUserMapper dcSysUserMapper;

    @Autowired
    RedisUtil redisUtil;

    @Override
    public RestfulMessage<String> addUser(UserRequest userRequest) {
        ...
    }
}

@ExtendWith(MockitoExtension.class)
class DcSysUserServiceImpl_MockTest {
    @Mock(answer = Answers.RETURNS_MOCKS)
    DcSysUserMapper dcSysUserMapper;

    @Mock(answer = Answers.RETURNS_MOCKS)
    RedisUtil redisUtil;
    //相当于RedisUtil redisUtil=mock(UserRequest.class,Answers.RETURNS_MOCKS)

    @InjectMocks
    DcSysUserServiceImpl dcSysUserServiceImpl;
    //相当于DcSysUserServiceImpl dcSysUserServiceImp=new DcSysUserServiceImpl(dcSysUserMapper,redisUtil)

    void addUser() {
        UserRequest userRequest = mock(UserRequest.class);
        when(dcSysUserMapper.selectOne(any())).thenReturn(null);
        when(dcSysUserMapper.insert(any())).thenReturn(1);
        dcSysUserServiceImpl.addUser(userRequest);
    }
}
```

>#### @Mock/mock()/@InjectMocks

待测试类DcSysUserServiceImpl里的依赖dcSysUserMapper、redisUtil需要使用@Mock注解

DcSysUserServiceImpl使用@InjectMocks注解

@Mock/mock调用返回mock对象，mock对象的方法返回值取决于方法返回值类型及@Mock/mock参数
|方法返回值类型|@Mock|@Mock(answer = Answers.RETURNS_MOCKS)|
|-|-|-|
boolean|false|false
数值类型及包装类| 0| 0
List、Map、数组|空容器|空容器
Object|null|mock对象|

>#### when()/doReturn()/doThrow() 指定mock对象的方法调用行为

```java
//第一次调用返回null 第二次返回1 之后调用都会报异常
when(dcSysUserMapper.selectOne(any()))
    .thenReturn(null)
    .thenReturn(1)
    .thenThrow(RuntimeException.class);

//语法不同 意思一样
doReturn(null).
doReturn(1).
doThrow(RuntimeException.class).
when(dcSysUserMapper)
.selectOne(any());

//有时候必须使用doReturn()/doThrow()，否则会报错，具体看官方文档
```

>####  @Spy/spy() spy对象除非用when()指定其行为 否则会调用实际方法

```java
    List list = new LinkedList();
    List spy = spy(list);

    //optionally, you can stub out some methods
    when(spy.size()).thenReturn(100);

    //using the spy calls real methods
    spy.add("one");
    spy.add("two");

    //prints "one" - the first element of a list
    System.out.println(spy.get(0));

    //size() method was stubbed - 100 is printed
    System.out.println(spy.size());
```

>## 4.SpringBootTest

```java

@SpringBootTest//使用此注解和@Autowired就能注入bean
@AutoConfigureMockMvc
class SsoControllerTest {

    @Autowired
    SsoController ssoController;

    @Autowired
    MockMvc mockMvc;
    @Value("${test.token}")
    String token;//在配置文件里写上token

    @Test
    void getSystemAuth() throws Exception {
        mockMvc.perform(get("/api/sso/getSystemAuth")
                        .cookie(new Cookie("token", token))
                )
                .andDo(print())
                .andExpect(status().isOk());
    }

    @Test
    void info() throws Exception {
        mockMvc.perform(post("/api/token/user/info")
                        .param("username", "cyyAdmin")
                        .cookie(new Cookie("token", token))
                        .header("from", "Y")
                        .contentType(MediaType.APPLICATION_JSON)
                        .content("{}")
                )
                .andDo(print())
                .andExpect(status().isOk());
    }
}

```
