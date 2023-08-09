- [ENGLISH](readme/README.en_US.md)
- [中文](readme/README.zh_CN.md)
# Dependency
```
        <dependency>
            <groupId>io.github.li-rixin</groupId>
            <artifactId>EntityStruct</artifactId>
            <version>1.1</version>
        </dependency>
```

# Explanation
1. Add the @ClassMapping annotation on entity classes to generate information for those classes during compilation.
2. Add the @FieldMapping annotation on entity class fields to specify the behavior of the fields.
3. The same "topic" points to the same generated class.
4. Use the "packageName" attribute to specify the package name for the generated classes. If not specified, they will be generated in the current package.
5. Use Lombok annotations to specify the Lombok annotations for the generated classes. If not specified, @Getter and @Setter annotations will be used by default. If specified, they will override the defaults.
6. After making changes, execute a build process to generate dynamic classes. Alternatively, enable automatic build in IntelliJ IDEA.
7. In the pom.xml, you can globally specify the default package name and default Lombok annotations for topics.

> The syntax for specifying default packages is -Aentitystruct.defaultPackage.{topic}={package}.
>
> The syntax for specifying default Lombok annotations is -Aentitystruct.defaultLombok.{topic}={full Lombok annotation names}.

For example, the following configuration specifies that the default package for the "vo" topic is "com.xiaoxin.vo", the default package for the "dto" topic is "com.xiaoxin.dto", and the default Lombok annotations for the "vo" topic are lombok.Setter and lombok.Getter. Additionally, it specifies that the package for "dto" is "com.xiaoxin.dto":

```
<build>
        <plugins>
          <!-- Other plugins -->
            <plugin>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <!-- Other configurations -->
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
