# JOOQ库版本导致的问题
- zipkinspans会依赖于JOOQ，有时候因为版本不同会报错`Cannot store spans.......due to VerifyError....ZipkinSpans overrides final method getSchema.....`
- 这就可以通过导入当前库`ZipkinSpans`类对应的JOOQ版本，比如说该项目的版本信息如下
``` java
@Generated(
    value = {
        "http://www.jooq.org",
        "jOOQ version:3.8.5"
    },
    comments = "This class is generated by jOOQ"
)
```
就可以通过导入相应版本的依赖解决
```xml
<dependency>
    <groupId>org.jooq</groupId>
    <artifactId>jooq</artifactId>
    <version>3.8.5</version>
</dependency>
```