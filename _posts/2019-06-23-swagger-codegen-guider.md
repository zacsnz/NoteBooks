---
title: Swagger Codegen 高效开发客户端对接服务端代码
date: 2019-06-23 21:23:00
categories:
- components
tags:
- spring
- swagger
---

本文的目的是通过介绍swagger-codegen来高效开发客户端对接服务端代码。

--

# [Swagger] Swagger Codegen 高效开发客户端对接服务端代码
@[TOC](目录)

> 手机用户请`横屏`获取最佳阅读体验，`REFERENCES`中是本文参考的链接，如需要链接和更多资源，可以关注其他博客发布地址。

| 平台     | 地址                                   |
| -------- | -------------------------------------- |
| CSDN     | https://blog.csdn.net/sinat_28690417   |
| 简书     | https://www.jianshu.com/u/3032cc862300 |
| 个人博客 | https://yiyuery.club  |


> 本文的目的是通过介绍swagger-codegen来高效开发客户端对接服务端代码。

## 代码生成器

- 远端swagger.json

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-c12e222f147d8c07?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

```cmd
java -jar swagger-codegen-cli-2.4.5.jar generate -i http://localhost:9000/swagger-resources/v2/api-docs?group=UI -l java -o user-demo
```

- 本地文件

```java
java -jar swagger-codegen-cli-2.4.5.jar generate -i swagger/swagger.json -l java -o user-demo
```

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-4592dd3a0f49d360?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

`user-demo`

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-4eeca6a6845dc5b4?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-90cafe8b7c213c3b?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 自动生成

- 请求返回体

```java
/*
 * 前端接口说明书V1.0.0
 * 前端UI接口
 *
 * OpenAPI spec version: V1.0.0
 * Contact: xx@xx.com
 *
 * NOTE: This class is auto generated by the swagger code generator program.
 * https://github.com/swagger-api/swagger-codegen.git
 * Do not edit the class manually.
 */


package io.swagger.client;

import java.util.List;
import java.util.Map;

/**
 * API response returned by API call.
 *
 * @param <T> The type of data that is deserialized from response body
 */
public class ApiResponse<T> {
    final private int statusCode;
    final private Map<String, List<String>> headers;
    final private T data;

    /**
     * @param statusCode The status code of HTTP response
     * @param headers The headers of HTTP response
     */
    public ApiResponse(int statusCode, Map<String, List<String>> headers) {
        this(statusCode, headers, null);
    }

    /**
     * @param statusCode The status code of HTTP response
     * @param headers The headers of HTTP response
     * @param data The object deserialized from response bod
     */
    public ApiResponse(int statusCode, Map<String, List<String>> headers, T data) {
        this.statusCode = statusCode;
        this.headers = headers;
        this.data = data;
    }

    public int getStatusCode() {
        return statusCode;
    }

    public Map<String, List<String>> getHeaders() {
        return headers;
    }

    public T getData() {
        return data;
    }
}

```

- 人员接口请求代理类

```java
/*
 * 前端接口说明书V1.0.0
 * 前端UI接口
 *
 * OpenAPI spec version: V1.0.0
 * Contact: xx@xx.com
 *
 * NOTE: This class is auto generated by the swagger code generator program.
 * https://github.com/swagger-api/swagger-codegen.git
 * Do not edit the class manually.
 */


package io.swagger.client.api;

import io.swagger.client.ApiCallback;
import io.swagger.client.ApiClient;
import io.swagger.client.ApiException;
import io.swagger.client.ApiResponse;
import io.swagger.client.Configuration;
import io.swagger.client.Pair;
import io.swagger.client.ProgressRequestBody;
import io.swagger.client.ProgressResponseBody;

import com.google.gson.reflect.TypeToken;

import java.io.IOException;


import io.swagger.client.model.User;

import java.lang.reflect.Type;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public class UserResourceControllerApi {
    private ApiClient apiClient;

    public UserResourceControllerApi() {
        this(Configuration.getDefaultApiClient());
    }

    public UserResourceControllerApi(ApiClient apiClient) {
        this.apiClient = apiClient;
    }

    public ApiClient getApiClient() {
        return apiClient;
    }

    public void setApiClient(ApiClient apiClient) {
        this.apiClient = apiClient;
    }

    /**
     * Build call for infoUsingGET
     * @param progressListener Progress listener
     * @param progressRequestListener Progress request listener
     * @return Call to execute
     * @throws ApiException If fail to serialize the request body object
     */
    public com.squareup.okhttp.Call infoUsingGETCall(final ProgressResponseBody.ProgressListener progressListener, final ProgressRequestBody.ProgressRequestListener progressRequestListener) throws ApiException {
        Object localVarPostBody = null;

        // create path and map variables
        String localVarPath = "/swagger-resource/user/info";

        List<Pair> localVarQueryParams = new ArrayList<Pair>();
        List<Pair> localVarCollectionQueryParams = new ArrayList<Pair>();

        Map<String, String> localVarHeaderParams = new HashMap<String, String>();

        Map<String, Object> localVarFormParams = new HashMap<String, Object>();

        final String[] localVarAccepts = {
            "*/*"
        };
        final String localVarAccept = apiClient.selectHeaderAccept(localVarAccepts);
        if (localVarAccept != null) localVarHeaderParams.put("Accept", localVarAccept);

        final String[] localVarContentTypes = {

        };
        final String localVarContentType = apiClient.selectHeaderContentType(localVarContentTypes);
        localVarHeaderParams.put("Content-Type", localVarContentType);

        if(progressListener != null) {
            apiClient.getHttpClient().networkInterceptors().add(new com.squareup.okhttp.Interceptor() {
                @Override
                public com.squareup.okhttp.Response intercept(com.squareup.okhttp.Interceptor.Chain chain) throws IOException {
                    com.squareup.okhttp.Response originalResponse = chain.proceed(chain.request());
                    return originalResponse.newBuilder()
                    .body(new ProgressResponseBody(originalResponse.body(), progressListener))
                    .build();
                }
            });
        }

        String[] localVarAuthNames = new String[] {  };
        return apiClient.buildCall(localVarPath, "GET", localVarQueryParams, localVarCollectionQueryParams, localVarPostBody, localVarHeaderParams, localVarFormParams, localVarAuthNames, progressRequestListener);
    }

    @SuppressWarnings("rawtypes")
    private com.squareup.okhttp.Call infoUsingGETValidateBeforeCall(final ProgressResponseBody.ProgressListener progressListener, final ProgressRequestBody.ProgressRequestListener progressRequestListener) throws ApiException {


        com.squareup.okhttp.Call call = infoUsingGETCall(progressListener, progressRequestListener);
        return call;

    }

    /**
     * info
     *
     * @return User
     * @throws ApiException If fail to call the API, e.g. server error or cannot deserialize the response body
     */
    public User infoUsingGET() throws ApiException {
        ApiResponse<User> resp = infoUsingGETWithHttpInfo();
        return resp.getData();
    }

    /**
     * info
     *
     * @return ApiResponse&lt;User&gt;
     * @throws ApiException If fail to call the API, e.g. server error or cannot deserialize the response body
     */
    public ApiResponse<User> infoUsingGETWithHttpInfo() throws ApiException {
        com.squareup.okhttp.Call call = infoUsingGETValidateBeforeCall(null, null);
        Type localVarReturnType = new TypeToken<User>(){}.getType();
        return apiClient.execute(call, localVarReturnType);
    }

    /**
     * info (asynchronously)
     *
     * @param callback The callback to be executed when the API call finishes
     * @return The request call
     * @throws ApiException If fail to process the API call, e.g. serializing the request body object
     */
    public com.squareup.okhttp.Call infoUsingGETAsync(final ApiCallback<User> callback) throws ApiException {

        ProgressResponseBody.ProgressListener progressListener = null;
        ProgressRequestBody.ProgressRequestListener progressRequestListener = null;

        if (callback != null) {
            progressListener = new ProgressResponseBody.ProgressListener() {
                @Override
                public void update(long bytesRead, long contentLength, boolean done) {
                    callback.onDownloadProgress(bytesRead, contentLength, done);
                }
            };

            progressRequestListener = new ProgressRequestBody.ProgressRequestListener() {
                @Override
                public void onRequestProgress(long bytesWritten, long contentLength, boolean done) {
                    callback.onUploadProgress(bytesWritten, contentLength, done);
                }
            };
        }

        com.squareup.okhttp.Call call = infoUsingGETValidateBeforeCall(progressListener, progressRequestListener);
        Type localVarReturnType = new TypeToken<User>(){}.getType();
        apiClient.executeAsync(call, localVarReturnType, callback);
        return call;
    }
}

```

- Model类

```JAVA
/*
 * 前端接口说明书V1.0.0
 * 前端UI接口
 *
 * OpenAPI spec version: V1.0.0
 * Contact: xx@xx.com
 *
 * NOTE: This class is auto generated by the swagger code generator program.
 * https://github.com/swagger-api/swagger-codegen.git
 * Do not edit the class manually.
 */


package io.swagger.client.model;

import java.util.Objects;
import java.util.Arrays;
import com.google.gson.TypeAdapter;
import com.google.gson.annotations.JsonAdapter;
import com.google.gson.annotations.SerializedName;
import com.google.gson.stream.JsonReader;
import com.google.gson.stream.JsonWriter;
import io.swagger.annotations.ApiModel;
import io.swagger.annotations.ApiModelProperty;
import java.io.IOException;

/**
 * User
 */
@javax.annotation.Generated(value = "io.swagger.codegen.languages.JavaClientCodegen", date = "2019-06-22T23:50:55.799+08:00")
public class User {
  @SerializedName("name")
  private String name = null;

  public User name(String name) {
    this.name = name;
    return this;
  }

   /**
   * Get name
   * @return name
  **/
  @ApiModelProperty(value = "")
  public String getName() {
    return name;
  }

  public void setName(String name) {
    this.name = name;
  }


  @Override
  public boolean equals(java.lang.Object o) {
    if (this == o) {
      return true;
    }
    if (o == null || getClass() != o.getClass()) {
      return false;
    }
    User user = (User) o;
    return Objects.equals(this.name, user.name);
  }

  @Override
  public int hashCode() {
    return Objects.hash(name);
  }


  @Override
  public String toString() {
    StringBuilder sb = new StringBuilder();
    sb.append("class User {\n");

    sb.append("    name: ").append(toIndentedString(name)).append("\n");
    sb.append("}");
    return sb.toString();
  }

  /**
   * Convert the given object to string with each line indented by 4 spaces
   * (except the first line).
   */
  private String toIndentedString(java.lang.Object o) {
    if (o == null) {
      return "null";
    }
    return o.toString().replace("\n", "\n    ");
  }

}


```

## 项目内集成

> 依赖

```json
dependencies {
    compile localLibs['swagger-codegen-cli']
    testCompile libs['junit']
}

ext {
    ver = [
            swagger: [
                    asciidoctorj    : "1.5.6",
                    asciidoctorj_pdf: "1.5.0-alpha.10",
                    jruby_complete  : "1.7.21"
            ],
            util   : [
                    pdfbox             : "2.0.15",
                    swagger_codegen_cli: "2.4.5"
            ]
    ]

    localLibs = [
            "asciidoctorj"       : "org.asciidoctor:asciidoctorj:$ver.swagger.asciidoctorj",
            "asciidoctorj-pdf"   : "org.asciidoctor:asciidoctorj-pdf:$ver.swagger.asciidoctorj_pdf",
            "jruby-complete"     : "org.jruby:jruby-complete:$ver.swagger.jruby_complete",
            "pdfbox"             : "org.apache.pdfbox:pdfbox:$ver.util.pdfbox",
            "swagger-codegen-cli": "io.swagger:swagger-codegen-cli:$ver.util.swagger_codegen_cli"
    ]
}

```



```java
/*
 * @ProjectName: 编程学习
 * @Copyright:   2019 HangZhou xiazhaoyang Dev, Ltd. All Right Reserved.
 * @address:     https:yiyuery.club
 * @date:        2019/5/20 20:57
 * @email:       xiazhaoyang@live.com
 * @description: 本内容仅限于编程技术学习使用，转发请注明出处.
 */
package com.example.code;

import io.airlift.airline.Cli;
import io.airlift.airline.Help;
import io.swagger.codegen.cmd.*;

/**
 * <p>
 *
 * </p>
 *
 * @author xiazhaoyang
 * @version v1.0.0
 * @date 2019-06-12 22:26
 * @modificationHistory=========================逻辑或功能性重大变更记录
 * @modify By: {修改人} 2019-06-12
 * @modify reason: {方法名}:{原因}
 * ...
 */
public class SwaggerCodeGenApplication {

    public static void main(String[] args) {
        Cli.CliBuilder<Runnable> builder =
                Cli.<Runnable>builder("swagger-codegen-cli")
                        .withDescription(
                                String.format(
                                        "Swagger code generator CLI (version %s). More info on swagger.io",
                                        "2.4.5"))
                        .withDefaultCommand(Langs.class)
                        .withCommands(Generate.class, Meta.class, Langs.class, Help.class,
                                ConfigHelp.class, Validate.class, Version.class);

       // builder.build().parse(new String[]{"config-help", "-l" ,"java"}).run();
        builder.build().parse(new String[]{
                "generate",
                "-i",
                "/Users/xiazhaoyang/Downloads/code/swagger/swagger.json",
                "-l",
                "java",
                "-o",
                "/Users/xiazhaoyang/Capsule/workspace/ishare-project/swagger-enhanced/swagger-code-gen/out/production/user-demo"
        }).run();
        //java -jar swagger-codegen-cli-2.4.5.jar generator -i swagger/swagger.json -l java -o com/example/java
    }
}

```

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-5f58a8454d54d7ae?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

需要注意的是，自动生成的是客户端代码，请求`/swagger-resource/user/info`时，可以通过自动生成的代理类`UserResourceControllerApi`来完成。

```java
 public com.squareup.okhttp.Call infoUsingGETCall(final ProgressResponseBody.ProgressListener progressListener, final ProgressRequestBody.ProgressRequestListener progressRequestListener) throws ApiException {
        Object localVarPostBody = null;

        // create path and map variables
        String localVarPath = "/swagger-resource/user/info";

        List<Pair> localVarQueryParams = new ArrayList<Pair>();
        List<Pair> localVarCollectionQueryParams = new ArrayList<Pair>();

        Map<String, String> localVarHeaderParams = new HashMap<String, String>();

        Map<String, Object> localVarFormParams = new HashMap<String, Object>();

        final String[] localVarAccepts = {
            "*/*"
        };
        final String localVarAccept = apiClient.selectHeaderAccept(localVarAccepts);
        if (localVarAccept != null) localVarHeaderParams.put("Accept", localVarAccept);

        final String[] localVarContentTypes = {

        };
        final String localVarContentType = apiClient.selectHeaderContentType(localVarContentTypes);
        localVarHeaderParams.put("Content-Type", localVarContentType);

        if(progressListener != null) {
            apiClient.getHttpClient().networkInterceptors().add(new com.squareup.okhttp.Interceptor() {
                @Override
                public com.squareup.okhttp.Response intercept(com.squareup.okhttp.Interceptor.Chain chain) throws IOException {
                    com.squareup.okhttp.Response originalResponse = chain.proceed(chain.request());
                    return originalResponse.newBuilder()
                    .body(new ProgressResponseBody(originalResponse.body(), progressListener))
                    .build();
                }
            });
        }

        String[] localVarAuthNames = new String[] {  };
        return apiClient.buildCall(localVarPath, "GET", localVarQueryParams, localVarCollectionQueryParams, localVarPostBody, localVarHeaderParams, localVarFormParams, localVarAuthNames, progressRequestListener);
    }
```

> 测试代码

- 自动生成项目构建

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-a7ed58db3db86fec?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

配置仓库和本地java运行环境版本

初次请求失败，检查请求路径：

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-8adc30e784340688?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

本地提供`user-demo`的服务实际运行端口是9000，所以调整下配置

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-857a7fef9d9d7b13.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-ada351d78d7f4f44?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

检查后才发现，原来上图框起来的地方配置的端口是8000,所以生成的swagger.json也是默认basePath=localhost:8080,调整配置后重新生成代码，ApiClient的配置更新为`https://localhost:9000/swagger-resources`

```java
public static void main(String[] args) {
    Cli.CliBuilder<Runnable> builder =
            Cli.<Runnable>builder("swagger-codegen-cli")
                    .withDescription(
                            String.format(
                                    "Swagger code generator CLI (version %s). More info on swagger.io",
                                    "2.4.5"))
                    .withDefaultCommand(Langs.class)
                    .withCommands(Generate.class, Meta.class, Langs.class, Help.class,
                            ConfigHelp.class, Validate.class, Version.class);

   // builder.build().parse(new String[]{"config-help", "-l" ,"java"}).run();
    builder.build().parse(new String[]{
            "generate",
            "-i",
            "http://localhost:9000/swagger-resources/v2/api-docs?group=UI",
            "-l",
            "java",
            "-o",
            "/Users/xiazhaoyang/Downloads/code/user-demo"
    }).run();
    //java -jar swagger-codegen-cli-2.4.5.jar generator -i swagger/swagger.json -l java -o com/example/java
}
```

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-85f0b7d242b23fe7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

再次尝试发起请求：

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-a63efaf4cced7ad4?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这个是因为提供的服务不是https协议的，我们手动修改`bathPath`

`private String basePath = "http://localhost:9000/swagger-resources";`

先测试下被请求资源是否正常

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-f2957bde5c769a23.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

通过测试用例访问：

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-e61afb999ddde985?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

可以看到客户端已经成功通过自动生成的代码完成对对服务端的调用。

## 总结

`swagger-codegen`的优点就是可以通过符合swagger规范的yaml或是json，来定义接口，并自动生成对应的客户端代码。

这个在接口开发(包括对接)工作中，是能够很大提升开发效率的事情。

除了文中的方式，swagger还支持自定义包名。具体可以参见[官网(GitHub)说明](https://github.com/swagger-api/swagger-codegen#getting-started)。

`Tips`，文中自己实现了一个提供swagger.json的服务，本地测试可以使用官网的地址

```json
http://petstore.swagger.io/v2/swagger.json
```

## REFRENCES

-  [swagger-codegen自动生成代码工具的介绍与使用](https://www.cnblogs.com/shamo89/p/7680771.html)
-  [swagger-codegen GitHub](https://github.com/swagger-api/swagger-codegen#getting-started)
-  [httpclient 错误 笔记](http://weikeqin.cn/2017/12/11/httpclient-error-notes/)


## 更多

> 扫码关注“架构探险之道”，回复`源码`，获取本文源码

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-209ab1eadce67808?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 知识星球(扫码加入获取历史源码和文章资源链接)

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/3734705-b409d937736fe0b8?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
