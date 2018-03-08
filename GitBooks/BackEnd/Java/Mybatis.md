# MyBatis
## 多个入参

1. xml配置文件
```xml
<insert id="mapCategoryAndPage" parameterType="map">
    INSERT INTO
        category_page_mapping (
            page_local_id,
            category_local_id)
    VALUES
        (#{pageLocalId},
         #{categoryLocalId});
</insert>
```
2. Java
```java
@Mapper
public interface MyMapper {

    void mapCategoryAndPage(
         @Param("categoryLocalId") Long categoryLocalId,
         @Param("pageLocalId") Long localId);

    ...
}
```
参考：[How can I pass multiple parameters and use them?](https://stackoverflow.com/questions/24968088/how-can-i-pass-multiple-parameters-and-use-them)
