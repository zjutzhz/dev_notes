# Nexus Repository

## Maven


## Ivy
在`~/.ivy2/ivysettings-public.xml`里新增如下内容：
```
<ivysettings>
  <resolvers>
    <ibiblio name="public" m2compatible="true" root="http://localhost:8081/content/groups/public"/>
  </resolvers>
</ivysettings>
```

## 参考
1. [Ivy via Nexus proxy
](https://stackoverflow.com/questions/1033859/ivy-via-nexus-proxy)
