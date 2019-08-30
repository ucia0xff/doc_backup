# 使用StringEscapeUtils类进行转义与反转义

---

## 引用

org.apache.commons.lang3.StringEscapeUtils已过时，需要替换成：
```java
import org.apache.commons.text.StringEscapeUtils;
```

## 使用

### 转义`<` `>` 等字符

```java
System.out.println(StringEscapeUtils.escapeHtml4("<>"));
```

结果：
```text
&lt;&gt;
```

### 反转义

```java
System.out.println(StringEscapeUtils.unescapeHtml4("&lt;&gt;"));
```

结果：
```text
<>
```