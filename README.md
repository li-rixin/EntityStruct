# 引入依赖
```
        <dependency>
            <groupId>io.github.li-rixin</groupId>
            <artifactId>EntityStruct</artifactId>
            <version>1.0.0</version>
        </dependency>
```

# 使用
1、在实体类上增加@ClassMapping注解可以编译生成该类的信息
2、在实体类字段增加@FieldMapping注解可以指定字段的行为
3、同一个topic指向同一个同一个生成类
4、在pom.xml可以统一指定topic的包位置和默认lombok注解
> 包语法格式为-Aentitystruct.defaultPackage.{topic}=指定topic所在包
> defaultLombok法格式为-Aentitystruct.defaultLombok.{topic}=指定topic默认的引入的lombok类
```
<build>
        <plugins>
          <!-- 其他插件-->
            <plugin>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <source>${maven.compiler.source}</source>
                    <target>${maven.compiler.target}</target>
                    <encoding>UTF-8</encoding>
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

