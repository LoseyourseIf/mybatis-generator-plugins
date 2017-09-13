# mybatis-generator-plugins
FORK自 KIWI 大神的 https://github.com/kiwiflydream/mybatis-generator-plugins
其中依赖的 mybatis-generator-core 修改成不生成 WithBlob 的 model https://github.com/LoseyourseIf/mybatis-generator-core

- pom.xml
``` xml
	<plugin>
                <groupId>org.mybatis.generator</groupId>
                <artifactId>mybatis-generator-maven-plugin</artifactId>
                <version>1.3.2</version>
                <configuration>
                    <configurationFile>src/main/resources/generator/generatorConfig.xml
                    </configurationFile>
                    <verbose>true</verbose>
                    <overwrite>true</overwrite>
                </configuration>
                <dependencies>
                    <dependency>
                        <groupId>xyz.mrwood.mybatis.generator.plugin</groupId>
                        <artifactId>mybatis-generator-plugin</artifactId>
                        <version>1.0</version>
                    </dependency>
                </dependencies>
            </plugin>
```

- generatorConfig.xml
``` xml
    <!-- 集成lombok -->
    <plugin type="xyz.mrwood.mybatis.generator.plugin.plugins.LombokPlugin"/>
    <!--生成拓展类-->
    <plugin type="xyz.mrwood.mybatis.generator.plugin.plugins.ExtPlugin" />
```


- 添加配置支持
``` xml
    <!-- 去除生成文件前缀 -->
    <property name="classRemovePrefix" value="Lp"/>
    <!-- 生成扩展类与xml的后缀 -->
    <property name="extClassSuffix" value="Ext"/>
    <!-- 给扩展类添加注解 -->
    <property name="extClassAddAnno" value="@Mapper"/>
    <!-- 给扩展类添加注解需要导入的类(import) -->
    <property name="extClassAddAnnoClass" value="org.apache.ibatis.annotations.Mapper"/>
    <!--每个字段添加数据库字段注释-->
    <plugin type="xyz.mrwood.mybatis.generator.plugin.plugins.CommentPlugin" />
```

- property
``` xml
<!--去除生成的类的前缀-->
<property name="classRemovePrefix" value="Lp"/>
<!--指定扩展类的后缀，默认是Ext-->
<property name="extClassSuffix" value="Ext"/>
<!--添加扩展类的注解-->
<property name="extClassAddAnno" value="@Mapper"/>
<!--添加扩展类的导入类,就是import信息-->
<property name="extClassAddAnnoClass" value="org.apache.ibatis.annotations.Mapper"/>
```
