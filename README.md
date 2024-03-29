# Asset Pipeline Thymeleaf Taglib

[![Maven Central](https://img.shields.io/maven-central/v/ch.itds.taglib/asset-pipeline-thymeleaf-taglib)](https://search.maven.org/remote_content?g=ch.itds.taglib&a=asset-pipeline-thymeleaf-taglib&v=LATEST)

## Usage

### Add dependency

```gradle
compile "ch.itds.taglib:asset-pipeline-thymeleaf-taglib:1.1.1"
```

### Usage in HTML/thymeleaf

```html
<!DOCTYPE html>
<html xmlns:asset="https://www.itds.ch/taglib/asset">
<script asset:src="@{/assets/main.js}"></script>
<link asset:href="@{/assets/main.css}" rel="stylesheet"/>
<meta name="msapplication-TileImage" th:content="${#asset.path('/assets/favicons/mstile-144x144.png')}"/>
</html>
```

### Register Dialect

If auto-configuration is disabled or not available you must register the dialect as follows:

```java
@Configuration
public class ThymeleafConfig {

    @Bean
    public AssetDialect assetDialect() {
        return new AssetDialect();
    }
}
```


## How it works

The attribute tag processors try to lookup the file in the generated manifest file. If the file is available the url is rewritten according to the manifest file.

If no entry is found (e.g. in development mode) the url is not modified.
