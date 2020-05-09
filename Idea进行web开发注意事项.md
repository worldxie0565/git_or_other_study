## idea终端乱码问题
Help --> Edit Custom VM Options... 最后添加一行 -Dfile.encoding=utf-8
## window&linux tomcat发布项目web项目注意事项
+ mysql 字符编码
+ mysql 大小写敏感

## ssm框架消息转换器
  在springmvc配置文件中添加    
```
    <!--开启注解-->
    <mvc:annotation-driven>
        <mvc:message-converters register-defaults="true">
            <ref bean="stringHttpMessageConverter"/>
            <ref bean="fastJsonHttpMessageConverter"/>
        </mvc:message-converters>
    </mvc:annotation-driven>

    <bean id="stringHttpMessageConverter"
          class="org.springframework.http.converter.StringHttpMessageConverter">
        <constructor-arg value="UTF-8" index="0"></constructor-arg>
        <property name="supportedMediaTypes">
            <list>
                <value>text/plain;charset=UTF-8</value>
            </list>
        </property>
    </bean>

    <bean id="fastJsonHttpMessageConverter" class="com.alibaba.fastjson.support.spring.FastJsonHttpMessageConverter4">
        <property name="supportedMediaTypes">
            <list>
                <value>text/html;charset=UTF-8</value>
                <value>application/json;charset=UTF-8</value>
            </list>
        </property>
        <property name="fastJsonConfig">
            <bean class="com.alibaba.fastjson.support.config.FastJsonConfig">
                <property name="features">
                    <list>
                        <value>AllowArbitraryCommas</value>
                        <value>AllowUnQuotedFieldNames</value>
                        <value>DisableCircularReferenceDetect</value>
                    </list>
                </property>
                <property name="dateFormat" value="yyyy-MM-dd HH:mm:ss"></property>
            </bean>
        </property>
    </bean>
```
