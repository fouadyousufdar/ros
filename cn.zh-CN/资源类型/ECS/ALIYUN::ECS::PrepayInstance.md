# ALIYUN::ECS::PrepayInstance {#concept_n23_ryt_qgb .concept}

ALIYUN::ECS::PrepayInstance类型用于创建预付费 ECS 实例。

## 语法 {#section_xyg_tn2_lfb .section}

``` {#codeblock_2uf_4b8_0kl .language-json}
{
  "Type": "ALIYUN::ECS::PrepayInstance",
  "Properties": {
    "PeriodType": String,
    "DedicatedHostId": String,
    "RamRoleName": String,
    "IoOptimized": Boolean,
    "InternetChargeType": String,
    "PrivateIpAddress": String,
    "KeyPairName": String,
    "SystemDiskDiskName": String,
    "PeriodUnit": String,
    "Description": String,
    "Tags": List,
    "MinAmount": Integer,
    "HostName": String,
    "AutoRenewPeriod": Number,
    "ImageId": String,
    "AutoRenew": Boolean,
    "InstanceChargeType": String,
    "VSwitchId": String,
    "Password": String,
    "InstanceType": String,
    "MaxAmount": Integer,
    "SystemDiskCategory": String,
    "SystemDiskSize": Number,
    "ZoneId": String,
    "InternetMaxBandwidthOut": Integer,
    "VpcId": String,
    "InstanceName": String,
    "InternetMaxBandwidthIn": Integer,
    "UserData": String,
    "DeploymentSetId": String,
    "SecurityGroupId": String,
    "Period": Number,
    "HpcClusterId": String,
    "AllocatePublicIP": Boolean,
    "SystemDiskDescription": String,
    "DiskMappings": List
  }
}
```

## 属性 {#section_cgd_53n_4fb .section}

|属性名称|类型|必须|允许更新|描述|约束|
|----|--|--|----|--|--|
|HpcClusterId|String|否|否|实例所属的EHPC集群ID。|无。|
|PeriodType|String|是|否|周期类型。|可用值：Monthly | Yearly|
|DedicatedHostId|String|否|否|是否在专有宿主机上创建 ECS 实例。|无|
|RamRoleName|String|否|否|实例RAM 角色名称。可以调用ListRoles查询。请参见[CreateRole](https://www.alibabacloud.com/help/doc-detail/28710.htm)和 [ListRoles](https://www.alibabacloud.com/help/doc-detail/28713.htm)|无|
|IoOptimized|Boolean|否|否| 是否为I/O优化实例。

 [已停售的实例规格](https://www.alibabacloud.com/help/faq-detail/55263.htm)实例默认值：none

 其他实例规格默认值：optimized

 |取值范围： -   none：非I/O优化
-   optimized：I/O优化

 |
|InternetChargeType|String|否|否| 网络计费类型。

 默认值：PayByBandwidth

 |取值范围： -   PayByBandwidth：按固定带宽计费
-   PayByTraffic：按使用流量计费

 |
|PrivateIpAddress|String|否|否|实例私网IP地址。该IP地址必须为 `VSwitchId` 网段的子集网址。|无|
|KeyPairName|String|否|否|密钥对名称。 -   Windows实例，忽略该参数。默认为空。即使填写了该参数，仍旧只执行 `Password` 的内容。
-   Linux实例的密码登录方式会被初始化成禁止。

 |无|
|SystemDiskDiskName|String|否|否|系统盘名称。|无|
|PeriodUnit|String|否|否|购买资源的时长。 `PeriodUnit` 为 `Week` 时：

 -   Period 取值 \{“1”, “2”, “3”, “4”\}
-   AutoRenewPeriod 取值 \{“1”, “2”, “3”\}

 `PeriodUnit` 为 `Month` 时： -   Period 取值 \{ “1”, “2”, “3”, “4”, “5”, “6”, “7”, “8”, “9”, “12”, “24”, “36”,”48”,”60”\}
-   AutoRenewPeriod 取值 \{“1”, “2”, “3”, “6”, “12”\}

 默认值：Month|可选值：Week | Month。|
|Description|String|否|否| 实例的描述。

 取值范围：\[2,256\]，默认值为空。

 |无|
|Tags|List|否|否|用户自定义标签。|最大20个。|
|MinAmount|Integer|是|否| 创建的实例的最小数量。

 默认值：1。

 |可用范围：1-100。|
|HostName|String|否|否|云服务器的主机名。 -   点号（.）和短横线（-）不能作为首尾字符，更不能连续使用。
-   Windows 实例：字符长度为 \[2, 15\]，不支持点号（.），不能全是数字。允许大小写英文字母、数字和短横线（-）。
-   其他类型实例（Linux 等）：字符长度为 \[2, 64\]，支持多个点号（.），点之间为一段，每段允许大小写英文字母、数字和短横线（-）。

 |无|
|AutoRenewPeriod|Number|否|否|每次自动续费的时长，当参数`AutoRenew`取值`True`时为必填。|取值范围：1 | 2 | 3 | 6 |12|
|ImageId|String|是|是| 镜像文件 ID，启动实例时选择的镜像资源。

 您可以通过 [DescribeImages](https://www.alibabacloud.com/help/doc-detail/25534.htm) 查询您可以使用的镜像资源。

 如需使用云市场镜像，您可以在云市场镜像商详情页查看ImageId。

 |无|
|AutoRenew|Boolean|否|否|是否要自动续费。当参数 `InstanceChargeType` 取值 `PrePaid` 时才生效。取值范围： -   True：自动续费。
-   False（默认）：不自动续费。

 默认值：False。|无|
|InstanceChargeType|String|否|否|实例的付费方式。|取值范围： -   PrePaid：预付费，包年包月。选择该类付费方式时，您必须确认自己的账号支持余额支付/信用支付，否则将返回 `InvalidPayMethod` 的错误提示。
-   PostPaid（默认）：按量付费。

 |
|VSwitchId|String|否|否|如果是创建VPC类型的实例，需要指定虚拟交换机ID。|无|
|Password|String|否|是|实例的密码。长度为 8 至 30 个字符，必须同时包含大小写英文字母、数字和特殊符号。特殊符号可以是\(\)\` ~!@\#$%^&\*-\_+=|\{\}\[\]:;‘<\>,.?/。其中，Windows 实例不能以斜线号（/）为密码首字符。|无|
|InstanceType|String|是|否|实例的资源规格。更多详情，请参见 [ECS实例规格](https://www.alibabacloud.com/help/doc-detail/25378.htm)，也可以调用 [DescribeInstanceTypes](https://www.alibabacloud.com/help/doc-detail/25620.htm) 接口获得最新的规格表。|无|
|MaxAmount|Integer|是|否|创建的实例的最大数量。|可用范围：1-100。|
|SystemDiskCategory|String|否|否| 系统盘的磁盘种类。

 已停售的实例规格且非 I/O 优化实例默认值：cloud

 否则，默认值：cloud\_efficiency

 |取值范围： -   cloud：普通云盘
-   cloud\_efficiency：高效云盘
-   cloud\_ssd：SSD 云盘
-   ephemeral\_ssd：本地 SSD 盘

 |
|SystemDiskSize|Number|否|是|系统盘大小，单位为GiB。 该参数的取值必须大于或者等于max\{20, ImageSize\}。

 默认值：max\{40, ImageSize\}

 |取值范围：\[20, 500\]|
|ZoneId|String|否|否|实例所属的可用区编号。更多详情，请参阅 [DescribeZones](https://www.alibabacloud.com/help/doc-detail/25610.htm) 获取可用区列表。 空表示由系统选择，默认值：空。

 |无|
|InternetMaxBandwidthOut|Integer|否|否|公网出带宽最大值，单位为Mbit/s。| 按固定带宽计费时取值范围：\[0, 200\]，默认值为 0。

 按流量计费时取值范围：\[1, 200\]，必须指定数值。

 |
|VpcId|String|否|否|VPC id。|无|
|InstanceName|String|否|否|实例的名称。|最长 128 个字符，可包含英文、中文、数字、下划线（\_）、点（.）、连字符（-）。|
|InternetMaxBandwidthIn|Integer|否|否|公网入带宽最大值，单位为Mbit/s。默认值：200|取值范围：\[1,200\]|
|UserData|String|否|是|创建 ECS 实例时传递的用户数据。|内容需要限制在16KB以内，不需要Base64，特殊字符需要使用 "\\" 转译。|
|SecurityGroupId|String|否|否|指定新创建实例所属于的安全组代码，同一个安全组内的实例之间可以互相访问。|无|
|Period|Number|是|否|购买资源的时长，单位为：月。当参数 `InstanceChargeType` 取值为 `PrePaid` 时才生效且为必选值。一旦指定了 DedicatedHostId，则取值范围不能超过专有宿主机的订阅时长。|取值范围： -   `PeriodUnit=Week`时，Period取值：\{“1”, “2”, “3”, “4”\}
-   `PeriodUnit=Month`时，Period取值：\{ “1”, “2”, “3”, “4”, “5”, “6”, “7”, “8”, “9”, “12”, “24”, “36”,”48”,”60”\}

 |
|AllocatePublicIP|Boolean|否|否|指定是否创建公网 IP。如果 `InternetMaxBandwidthOut` 设置为 0，不会分配公网 IP。默认值：True|无|
|SystemDiskDescription|String|否|否|系统盘描述信息。|无|
|DiskMappings|List|否|否|指定需要挂载的磁盘。|最多支持 16块磁盘。|
|DeploymentSetId|String|否|否|部署集 ID。|无。|

## Tags语法 {#section_c9a_fm3_mv0 .section}

``` {#codeblock_hw0_x4p_935}
"Tags": [
  {
    "Key": String,
    "Value": String
  }
]
```

## Tags属性 {#section_ffh_ccm_70r .section}

|属性名称|类型|必须|允许更新|描述|约束|
|----|--|--|----|--|--|
|Key|String|是|否|无。|无。|
|Value|String|否|否|无。|无。|

## DiskMappings语法 {#section_tg6_f51_eav .section}

``` {#codeblock_b6j_far_o87}
"DiskMappings": [
  {
    "Category": String,
    "DiskName": String,
    "Description": String,
    "Device": String,
    "SnapshotId": String,
    "Size": String
  }
]
```

## DiskMappings属性 {#section_o6l_y34_56i .section}

|**属性名称**|**类型**|**必须**|**允许更新**|**描述**|**约束**|
|--------|------|------|--------|------|------|
|Category|String|否|否|数据盘的类型。| 可选值：cloud、cloud\_efficiency、cloud\_ssd、ephemeral\_ssd。

 默认值：cloud\_efficiency。

 |
|DiskName|String|否|否|数据盘的名称。|最长 128 个字符，可包含英文、中文、数字、下划线（\_）、点（.）、连字符（-）。|
|Description|String|否|否|描述信息。|取值范围：\[2,256\]，默认值为空。|
|Device|String|否|否|指定数据盘的设备名称。|如不指定，则默认由系统按顺序分配，即从/dev/xvdb到/dev/xvdz。|
|SnapshotId|String|否|否|创建数据盘使用的快照。|无|
|Size|String|是|否|数据盘大小，单位：GB。|无|

## 返回值 {#section_fsg_t4n_4fb .section}

**Fn::GetAtt**

-   OrderId: 订单ID。
-   InnerIps: Classic 类型实例的私网 IP列表。当NetworkType为 Classic 时，该参数生效。
-   PrivateIps: VPC 类型实例的私网 IP列表。当NetworkType为 VPC 时，该参数生效。
-   ZoneIds: 可用区 ID列表。
-   PublicIps: Classic 类型实例的公网 IP 列表。当NetworkType为 Classic 时，该参数生效。
-   HostNames: 主机名列表。
-   RelatedOrderIds: 相关订单ID列表。
-   InstanceIds: 实例 ID列表。由系统生成，实例的全局唯一标识。

## 示例 {#section_klp_54n_4fb .section}

``` {#codeblock_xxm_3ts_jop}
{
  "ROSTemplateFormatVersion": "2015-09-01",
  "Parameters": {
    "PeriodType": {
      "Type": "String",
      "Description": "Charge period for created instances.",
      "AllowedValues": [
        "Monthly",
        "Yearly"
      ]
    },
    "DedicatedHostId": {
      "Type": "String",
      "Description": "which dedicated host will be deployed"
    },
    "PrivateIpAddress": {
      "Type": "String",
      "Description": "Private IP for the instance created. Only works for VPC instance and cannot duplicated with existing instance."
    },
    "Description": {
      "Type": "String",
      "Description": "Description of the instance, [2, 256] characters. Do not fill or empty, the default is empty."
    },
    "DiskMappings": {
      "Type": "CommaDelimitedList",
      "Description": "Disk mappings to attach to instance. Max support 16 disks.\nIf the image contains a data disk, you can specify other parameters of the data disk via the same value of parameter \"Device\". If parameter \"Category\" is not specified, it will be cloud_efficiency instead of \"Category\" of data disk in the image.",
      "MaxLength": 16
    },
    "SystemDiskSize": {
      "Type": "Number",
      "Description": "Disk size of the system disk, range from 20 to 500 GB. If you specify with your own image, make sure the system disk size bigger than image size. ",
      "MinValue": 20,
      "MaxValue": 500
    },
    "UserData": {
      "Type": "String",
      "Description": "User data to pass to instance. [1, 16KB] characters.User data should not be base64 encoded. If you want to pass base64 encoded string to the property, use function Fn::Base64Decode to decode the base64 string first."
    },
    "SystemDiskDescription": {
      "Type": "String",
      "Description": "Description of created system disk."
    },
    "InstanceChargeType": {
      "Type": "String",
      "Description": "Instance Charge type, allowed value: Prepaid and Postpaid. If specified Prepaid, please ensure you have sufficient balance in your account. Or instance creation will be failure. Default value is Postpaid.",
      "AllowedValues": [
        "PrePaid",
        "PostPaid"
      ],
      "Default": "PostPaid"
    },
    "AutoRenew": {
      "Type": "Boolean",
      "Description": "Auto renew the prepay instance. If the period type is by year, it will renew by year, else it will renew by month.",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ],
      "Default": false
    },
    "MaxAmount": {
      "Type": "Number",
      "Description": "Max number of instances to create, should be smaller than 'MaxAmount' and smaller than 100.",
      "MinValue": 1,
      "MaxValue": 100
    },
    "RamRoleName": {
      "Type": "String",
      "Description": "Instance RAM role name. The name is provided and maintained by Resource Access Management (RAM) and can be queried using ListRoles. For more information, see RAM API CreateRole and ListRoles."
    },
    "MinAmount": {
      "Type": "Number",
      "Description": "Max number of instances to create, should be bigger than 'MinAmount' and smaller than 100.",
      "MinValue": 1,
      "MaxValue": 100,
      "Default": 1
    },
    "ImageId": {
      "Type": "String",
      "Description": "Image ID to create ecs instance."
    },
    "SystemDiskDiskName": {
      "Type": "String",
      "Description": "Name of created system disk."
    },
    "InstanceType": {
      "Type": "String",
      "Description": "Ecs instance supported instance type, make sure it should be correct."
    },
    "AllocatePublicIP": {
      "Type": "Boolean",
      "Description": "The public ip for ecs instance, if properties is true, will allocate public ip. If property InternetMaxBandwidthOut set to 0, it will not assign public ip.",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ],
      "Default": true
    },
    "Tags": {
      "Type": "CommaDelimitedList",
      "Description": "Tags to attach to instance. Max support 20 tags to add during create instance. Each tag with two properties Key and Value, and Key is required.",
      "MaxLength": 20
    },
    "HostName": {
      "Type": "String",
      "Description": "Host name of created ecs instance. at least 2 characters, and '.' '-' Is not the first and last characters as hostname, not continuous use. Windows platform can be up to 15 characters, allowing letters (without limiting case), numbers and '-', and does not support the number of points, not all is digital ('.').Other (Linux, etc.) platform up to 30 characters, allowing support number multiple points for the period between the points, each permit letters (without limiting case), numbers and '-' components."
    },
    "Password": {
      "Type": "String",
      "Description": "Password of created ecs instance. Must contain at least 3 types of special character, lower character, upper character, number."
    },
    "AutoRenewPeriod": {
      "Type": "Number",
      "Description": "The time period of auto renew. When the parameter InstanceChargeType is PrePaid, it will take effect.It could be 1, 2, 3, 6, 12. Default value is 1.",
      "AllowedValues": [
        1,
        2,
        3,
        6,
        12
      ],
      "Default": 1
    },
    "KeyPairName": {
      "Type": "String",
      "Description": "SSH key pair name."
    },
    "IoOptimized": {
      "Type": "Boolean",
      "Description": "The 'optimized' instance can provide better IO performance. Support true or false, Default is true. ",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ],
      "Default": true
    },
    "ZoneId": {
      "Type": "String",
      "Description": "current zone to create the instance."
    },
    "VSwitchId": {
      "Type": "String",
      "Description": "The vSwitch Id to create ecs instance."
    },
    "SecurityGroupId": {
      "Type": "String",
      "Description": "Security group to create ecs instance. For classic instance need the security group not belong to VPC, for VPC instance, please make sure the security group belong to specified VPC."
    },
    "Period": {
      "Type": "Number",
      "Description": "Prepaid time period. While choose by pay by month, it could be from 1 to 9. While choose pay by year, it could be from 1 to 3.",
      "MinValue": 1,
      "MaxValue": 9,
      "Default": 1
    },
    "InternetChargeType": {
      "Type": "String",
      "Description": "Instance internet access charge type.Support 'PayByBandwidth' and 'PayByTraffic' only. For AfterPay instance, default is 'PayByBandwidth'.",
      "AllowedValues": [
        "PayByBandwidth",
        "PayByTraffic"
      ],
      "Default": "PayByBandwidth"
    },
    "SystemDiskCategory": {
      "Type": "String",
      "Description": "Category of system disk. Default is cloud_efficiency. support cloud|cloud_efficiency|cloud_ssd|ephemeral_ssd",
      "AllowedValues": [
        "cloud",
        "cloud_efficiency",
        "cloud_ssd",
        "ephemeral_ssd"
      ],
      "Default": "cloud_efficiency"
    },
    "InstanceName": {
      "Type": "String",
      "Description": "Display name of the instance, [2, 128] English or Chinese characters, must start with a letter or Chinese in size, can contain numbers, '_' or '.', '-'"
    },
    "InternetMaxBandwidthOut": {
      "Type": "Number",
      "Description": "Set internet output bandwidth of instance. Unit is Mbps(Mega bit per second). Range is [0,200]. Default is 1.While the property is not 0, public ip will be assigned for instance.",
      "MinValue": 0,
      "MaxValue": 200,
      "Default": 1
    },
    "VpcId": {
      "Type": "String",
      "Description": "The VPC id to create ecs instance."
    },
    "InternetMaxBandwidthIn": {
      "Type": "Number",
      "Description": "Max internet out band width setting, unit in Mbps(Mega bit per second). The range is [1,200], default is 200 Mbps.",
      "MinValue": 1,
      "MaxValue": 200,
      "Default": 200
    },
    "PeriodUnit": {
      "Type": "String",
      "Description": "Unit of prepaid time period, it could be Week/Month. Default value is Month.",
      "AllowedValues": [
        "Week",
        "Month"
      ],
      "Default": "Month"
    }
  },
  "Resources": {
    "PrepayInstance": {
      "Type": "ALIYUN::ECS::PrepayInstance",
      "Properties": {
        "PeriodType": {
          "Ref": "PeriodType"
        },
        "DedicatedHostId": {
          "Ref": "DedicatedHostId"
        },
        "PrivateIpAddress": {
          "Ref": "PrivateIpAddress"
        },
        "Description": {
          "Ref": "Description"
        },
        "DiskMappings": {
          "Fn::Split": [
            ",",
            {
              "Ref": "DiskMappings"
            },
            {
              "Ref": "DiskMappings"
            }
          ]
        },
        "SystemDiskSize": {
          "Ref": "SystemDiskSize"
        },
        "UserData": {
          "Ref": "UserData"
        },
        "SystemDiskDescription": {
          "Ref": "SystemDiskDescription"
        },
        "InstanceChargeType": {
          "Ref": "InstanceChargeType"
        },
        "AutoRenew": {
          "Ref": "AutoRenew"
        },
        "MaxAmount": {
          "Ref": "MaxAmount"
        },
        "RamRoleName": {
          "Ref": "RamRoleName"
        },
        "MinAmount": {
          "Ref": "MinAmount"
        },
        "ImageId": {
          "Ref": "ImageId"
        },
        "SystemDiskDiskName": {
          "Ref": "SystemDiskDiskName"
        },
        "InstanceType": {
          "Ref": "InstanceType"
        },
        "AllocatePublicIP": {
          "Ref": "AllocatePublicIP"
        },
        "Tags": {
          "Fn::Split": [
            ",",
            {
              "Ref": "Tags"
            },
            {
              "Ref": "Tags"
            }
          ]
        },
        "HostName": {
          "Ref": "HostName"
        },
        "Password": {
          "Ref": "Password"
        },
        "AutoRenewPeriod": {
          "Ref": "AutoRenewPeriod"
        },
        "KeyPairName": {
          "Ref": "KeyPairName"
        },
        "IoOptimized": {
          "Ref": "IoOptimized"
        },
        "ZoneId": {
          "Ref": "ZoneId"
        },
        "VSwitchId": {
          "Ref": "VSwitchId"
        },
        "SecurityGroupId": {
          "Ref": "SecurityGroupId"
        },
        "Period": {
          "Ref": "Period"
        },
        "InternetChargeType": {
          "Ref": "InternetChargeType"
        },
        "SystemDiskCategory": {
          "Ref": "SystemDiskCategory"
        },
        "InstanceName": {
          "Ref": "InstanceName"
        },
        "InternetMaxBandwidthOut": {
          "Ref": "InternetMaxBandwidthOut"
        },
        "VpcId": {
          "Ref": "VpcId"
        },
        "InternetMaxBandwidthIn": {
          "Ref": "InternetMaxBandwidthIn"
        },
        "PeriodUnit": {
          "Ref": "PeriodUnit"
        }
      }
    }
  },
  "Outputs": {
    "PublicIps": {
      "Description": "Public IP address list of created ecs instance.",
      "Value": {
        "Fn::GetAtt": [
          "PrepayInstance",
          "PublicIps"
        ]
      }
    },
    "RelatedOrderIds": {
      "Description": "The related order id list of created ecs instances",
      "Value": {
        "Fn::GetAtt": [
          "PrepayInstance",
          "RelatedOrderIds"
        ]
      }
    },
    "PrivateIps": {
      "Description": "Private IP address list of created ecs instance. Only for VPC instance.",
      "Value": {
        "Fn::GetAtt": [
          "PrepayInstance",
          "PrivateIps"
        ]
      }
    },
    "HostNames": {
      "Description": "Host names of created instance.",
      "Value": {
        "Fn::GetAtt": [
          "PrepayInstance",
          "HostNames"
        ]
      }
    },
    "InnerIps": {
      "Description": "Inner IP address list of the specified instance. Only for classical instance.",
      "Value": {
        "Fn::GetAtt": [
          "PrepayInstance",
          "InnerIps"
        ]
      }
    },
    "ZoneIds": {
      "Description": "Zone id of created instance.",
      "Value": {
        "Fn::GetAtt": [
          "PrepayInstance",
          "ZoneIds"
        ]
      }
    },
    "OrderId": {
      "Description": "The order id list of created instance.",
      "Value": {
        "Fn::GetAtt": [
          "PrepayInstance",
          "OrderId"
        ]
      }
    },
    "InstanceIds": {
      "Description": "The instance id list of created ecs instance",
      "Value": {
        "Fn::GetAtt": [
          "PrepayInstance",
          "InstanceIds"
        ]
      }
    }
  }
}
```

