#

```java
Escaper HTML_ESCAPER =
      Escapers.builder()
          .addEscape('"', "&quot;")
          // Note: "&apos;" is not defined in HTML 4.01.
          .addEscape('\'', "&#39;")
          .addEscape('&', "&amp;")
          .addEscape('<', "&lt;")
          .addEscape('>', "&gt;")
          .build();
```
