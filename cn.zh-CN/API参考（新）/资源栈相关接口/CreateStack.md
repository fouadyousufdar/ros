# CreateStack {#doc_api_ROS_CreateStack .reference}

创建资源栈。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=ROS&api=CreateStack&type=RPC&version=2019-09-10)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateStack|系统规定参数。取值：CreateStack。

 |
|RegionId|String|是|cn-hangzhou|资源栈所属的地域ID。您可以调用[DescribeRegions](~~131035~~)查看最新的阿里云地域列表。

 |
|StackName|String|是|MyStack|资源栈名称。资源栈名称可以包含数字、字母（大小写敏感）、连字符、下划线。必须以数字或字母开头，且长度不超过255个字符。

 |
|TimeoutInMinutes|Long|是|10|创建资源栈的超时时间，以分钟为单位。

 默认值为 10。

 |
|Parameters.N.ParameterKey|String|否|InstanceId|参数的名称。 如果未指定特定参数的名称和值，则ROS将使用模板中指定的默认值。

 N最大值为200。

 |
|Parameters.N.ParameterValue|String|否|i-xxxxxx|参数的值。

 N最大值为200。

 |
|DisableRollback|Boolean|否|false|当创建资源栈失败时，是否禁用回滚策略，默认为 false。

 -   true 表示禁用回滚，即在创建资源栈失败时不会进行回滚；
-   false 表示不禁用回滚，即在创建资源栈失败时会进行回滚。

 |
|TemplateBody|String|否|\{ "ROSTemplateFormatVersion": "2015-09-01" \}|包含模板体的结构，最小长度为1个字节，最大长度为51,200个字节。

 您必须指定TemplateBody或TemplateURL参数，但不能同时指定两者。

 |
|StackPolicyURL|String|否|oss://ros-stack-policy/demo|包含资源栈策略的文件的位置。 URL必须指向位于Web服务器（http，https）中的策略（最大大小：16384字节），或阿里云OSS存储桶（例如oss://ros/stack-policy/demo、oss://ros/stack-policy/demo?RegionId=cn-hangzhou。oss地域如未指定，默认与接口参数RegionId相同。）。

 您可以指定StackPolicyBody或StackPolicyURL参数，但不能同时指定两者。

 URL最大长度为1350字节。

 |
|StackPolicyBody|String|否|\{"Statement": \[\{"Action": "Update:\*", "Resource": "\*", "Effect": "Allow", "Principal": "\*"\}\]\}|包含资源栈策略主体的结构，最小长度为1个字节，最大长度为16384个字节。

 您可以指定StackPolicyBody或StackPolicyURL参数，但不能同时指定两者。

 |
|NotificationURLs.N|RepeatList|否|http://my-site.com/ros-event|接收资源栈事件的URL回调地址。仅支持HTTP POST。

 N最大值为5，每个URL的最大长度为1024。

 |
|TemplateURL|String|否|oss://ros-template/demo|包含模板主体的文件的位置。 URL必须指向位于http Web服务器（http，https），或阿里云OSS存储桶（例如oss://ros/template/demo、oss://ros/template/demo?RegionId=cn-hangzhou。oss地域如未指定，默认与接口参数RegionId相同。）中的模板（最大大小：524288字节）。

 您必须指定TemplateBody或TemplateURL参数，但不能同时指定两者。

 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求的幂等性。 该值由客户端生成，并且必须是全局唯一的。 仅允许使用字母数字字符（区分大小写），连字符和下划线。 它最多可包含64个字符。更多详情，请参见[如何保证幂等性](~~134212~~)。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|StackId|String|4a6c9851-3b0f-4f5f-b4ca-a14bf691f2ff|资源栈ID。

 |
|RequestId|String|B288A0BE-D927-4888-B0F7-B35EF84B6E6F|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://ros.aliyuncs.com/?Action=CreateStack
&RegionId=cn-hangzhou
&StackName=MyStack
&Parameters.1.ParameterKey=InstanceId
&Parameters.1.ParameterValue=i-xxxxxx
&TimeoutInMinutes=10
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateStackResponse>
      <StackId>4a6c9851-3b0f-4f5f-b4ca-a14bf691f2ff</StackId>
      <RequestId>B288A0BE-D927-4888-B0F7-B35EF84B6E6F</RequestId>
</CreateStackResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"StackId":"4a6c9851-3b0f-4f5f-b4ca-a14bf691f2ff",
	"RequestId":"B288A0BE-D927-4888-B0F7-B35EF84B6E6F"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/ROS)查看更多错误码。

访问[公共错误码](~~131033~~)查看更多错误码。

|错误代码

|错误信息

|Http状态码

|描述

|
|------|------|---------|----|
|CircularDependency

|Circular Dependency Found: \{reason\}.

|400

|模板包含循环引用，reason为具体原因。

|
|InvalidSchema

|\{reason\}.

|400

|模板格式不正确，reason为具体原因。

|
|InvalidTemplateAttribute

|The Referenced Attribute \(\{resource\} \{name\}\) is incorrect.

|400

|模板包含不正确的资源属性\(输出\)引用，resource为资源名，name为属性名。

|
|InvalidTemplatePropertyType

|The specified value type of \(\{resource\} \{section\}\) is incorrect.

|400

|模板资源定义中，字段类型不正确，resource为资源名，section为字段名。

|
|InvalidTemplateReference

|The specified reference "\{name\}" \(in \{referencer\}\) is incorrect.

|400

|模板包含不正确的引用，name为引用名，referencer为引用者。

|
|InvalidTemplateSection

|The template section is invalid: \{section\}.

|400

|模板包含无效的字段，section为字段名。

|
|InvalidTemplateVersion

|The template version is invalid: \{reason\}.

|400

|模板版本不正确，reason为具体原因。

|
|StackValidationFailed

|\{reason\}.

|400

|资源栈校验失败，reason为具体原因。

|
|UnknownUserParameter

|The Parameter \(\{name\}\) was not defined in template.

|400

|传递的参数在模板中未定义，name为参数名。

|
|UserParameterMissing

|The Parameter \{name\} was not provided.

|400

|参数在模板中已定义，但未传递值，name为参数名。

|
|ActionInProgress

|Stack \{name\} already has an action \(\{action\}\) in progress.

|409

|资源栈在变更中，name为资源栈名称或ID，action为变更操作。

|
|StackExists

|The Stack \(\{name\}\) already exists.

|409

|同名资源栈已存在，name为资源栈名称。

|

