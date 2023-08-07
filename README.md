# 引入依赖
```
        <dependency>
            <groupId>io.github.li-rixin</groupId>
            <artifactId>EntityStruct</artifactId>
            <version>1.0.0</version>
        </dependency>
```

# 说明
1. 在实体类上增加@ClassMapping注解可以编译生成该类的信息
2. 在实体类字段增加@FieldMapping注解可以指定字段的行为
3. 同一个topic指向同一个同一个生成类
4. packageName指定生成的类的包名，无指定生成在当前包中
5. lombok注解指定生成的类的lombok注解，无指定默认为@Getter,@Setter,有指定则覆盖
6. 修改完成执行一些构建即可生成动态的类，或者idea打开自动构建
7. 在pom.xml可以统一指定topic的包名和默认lombok注解

   
> 指定默认包语法格式为-Aentitystruct.defaultPackage.{topic}=指定topic所在包
> 
> 指定默认lombok注解的语法格式为-Aentitystruct.defaultLombok.{topic}=指定topic默认的引入的lombok类完整名称

例如，以下指定了topic为vo的包的默认包为com.xiaoxin.dto，指定注解为lombok.Setter,lombok.Getter，指定dto的包为com.xiaoxin.dto
```
<build>
        <plugins>
          <!-- 其他插件-->
            <plugin>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <!--其他配置-->
                    <compilerArgs>
                        <arg>-Aentitystruct.defaultPackage.vo=com.xiaoxin.vo</arg>
                        <arg>-Aentitystruct.defaultPackage.dto=com.xiaoxin.dto</arg>
                        <arg>-Aentitystruct.defaultLombok.vo=lombok.Setter,lombok.Getter</arg>
                    </compilerArgs>
                </configuration>
            </plugin>
        </plugins>
    </build>
```

