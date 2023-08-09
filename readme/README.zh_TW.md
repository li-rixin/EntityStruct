- [简体中文](readme/README.zh_CN.md)
- [繁體中文](readme/README.zh_TW.md)
- [ENGLISH](readme/README.en_US.md)
# 引入依賴
```
        <dependency>
            <groupId>io.github.li-rixin</groupId>
            <artifactId>EntityStruct</artifactId>
            <version>1.1</version>
        </dependency>
```

# 說明
1. 在實體類上增加@ClassMapping註解可以編譯生成該類的信息。
2. 在實體類字段增加@FieldMapping註解可以指定字段的行為。
3. 同一個"topic"指向同一個生成的類。
4. 使用"packageName"屬性指定生成的類的包名。如果未指定，將在當前包中生成。
5. 使用Lombok註解來指定生成的類的Lombok註解。如果未指定，將默認使用@Getter和@Setter註解。如果指定，將覆蓋默認值。
6. 修改完成後，執行一些構建操作即可生成動態的類，或者在IntelliJ IDEA中開啟自動構建功能。
7. 在pom.xml中，您可以統一指定主題的默認包名和默認的Lombok註解。

> 指定默認包的語法格式是-Aentitystruct.defaultPackage.{topic}={package}。
>
> 指定默認的Lombok註解的語法格式是-Aentitystruct.defaultLombok.{topic}={完整的Lombok註解名稱}。

例如，以下配置指定了主題為"vo"的默認包為"com.xiaoxin.vo"，主題為"dto"的默認包為"com.xiaoxin.dto"，並且主題"vo"的默認Lombok註解為lombok.Setter和lombok.Getter。同時，它還指定了"dto"的包為"com.xiaoxin.dto"：

```
<build>
        <plugins>
          <!-- 其他插件 -->
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
