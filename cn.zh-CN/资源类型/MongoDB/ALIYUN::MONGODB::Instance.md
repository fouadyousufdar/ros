# ALIYUN::MONGODB::Instance {#concept_48464_zh .concept}

ALIYUN::MONGODB::Instance 类型用于创建云数据库 MongoDB 版实例。

## 语法 {#section_cfm_4m1_mfb .section}

``` {#codeblock_3i9_4t0_4gq .language-json}
{
  "Type": "ALIYUN::MONGODB::Instance",
  "Properties": {
    "SrcDBInstanceId": String,
    "ReplicationFactor": Integer,
    "DBInstanceStorage": Integer,
    "DBInstanceDescription": String,
    "SecurityIPArray": String,
    "ZoneId": String,
    "VpcId": String,
    "VSwitchId": String,
    "EngineVersion": String,
    "StorageEngine": String,
    "BackupId": String,
    "DBInstanceClass": String,
    "NetworkType": String,
    "AccountPassword": String,
    "DatabaseNames": String,
    "ReadonlyReplicas": Integer,
    "BusinessInfo": String,
    "ResourceGroupId": String,
    "AutoRenew": Boolean,
    "RestoreTime": String,
    "CouponNo": String,
    "Period": Integer,
    "ChargeType": String,
  }
}
```

## 属性 {#section_c7d_sst_8ix .section}

|属性名称|类型|必须|允许更新|描述|约束|
|----|--|--|----|--|--|
|DBInstanceStorage|Integer|是|否|指定数据库实例的大小。|取值范围：\[5,1000\]，单位是 GB。每 5 GB 递增 。|
|DBInstanceClass|String|是|否|指定数据库实例规格。|允许可选值：dds.mongo.mid（1核2G）、dds.mongo.standard（2核4G）、dds.mongo.large（4核8G）、 dds.mongo.xlarge（8核16G）、dds.mongo.2xlarge（8核32G）和 dds.mongo.4xlarge（16核64G）。|
|SrcDBInstanceId|String|否|否|通过备份实例创建的新实例。|无|
|DBInstanceDescription|String|否|否|指定实例的描述。|无|
|SecurityIPArray|String|否|否|指定所有可以访问该实例的 IP 名单| 以逗号隔开，不可重复，最多 1000 个。

 支持格式：%，0.0.0.0/0，10.23.12.24（IP），或者10.23.12.24/24（CIDR模式，无类域间路由，/24表示了地址中前缀的长度，范围\[1,32\]）。其中，0.0.0.0/0，表示不限制。

 默认为不限制。

 |
|ZoneId|String|否|否|指定可用区。|专有网络下要和 VSwitchId 的可用区一致。|
|VpcId|String|否|否|指定专有网络 ID 。|无|
|VSwitchId|String|否|否|指定 VpcId 下的虚拟交换机 ID。|无|
|BackupId|String|否|否|指定备份集 ID。|无|
|NetworkType|String|否|否|指定网络类型 。| 可选值： CLASSIC 和 VPC。

 默认值： CLASSIC。

 |
|AccountPassword|String|否|否|指定 Root 用户的密码。|密码由字母，数字和下划线（\_）组成；长度为 6-32 字符。|
|EngineVersion|String|否|否|数据库版本号。| 可用值：3.2 | 3.4 | 4.0 .

 默认值：3.4。

 |
|StorageEngine|String|否|否|存储引擎。| 可用值：WiredTiger | RocksDB。

 默认值：WiredTiger。

 |
|ReplicationFactor|String|否|否|副本集节点个数| 允许值：3、5、7。

 默认值：3。

 |
|DatabaseNames|String|否|否|数据库名|无|
|ReadonlyReplicas|Integer|否|否|只读节点的数量|可用值：1，2，3，4，5。|
|BusinessInfo|String|否|否|业务信息，是一个附加参数。|无|
|ResourceGroupId|String|否|否|资源组的ID。|无|
|AutoRenew|Boolen|否|否|指示是否为实例启用自动更新。默认值：false。|有效值： -   true：启用自动更新。
-   false：未启用自动更新。您必须手动更新实例。

 |
|RestoreTime|String|否|否|恢复克隆实例的时间。格式为yyyy-MM-ddTHH:mm:ssZ。此参数只能在调用此操作克隆实例时指定。您还必须指定SrcDBInstanceIdparameter和Backupidparameter。您可以克隆实例到过去七天中的任何恢复时间。|无|
|CouponNo|String|否|否|优惠券代码。默认值：youhuiquan\_promotion\_option\_id\_for\_blank。|无|
|Period|Integer|否|否|实例的订阅期。单位：月。有效值:\[1~9\]，12,24,36。默认为1。|可用值: 1，2，3，4，5，6，7，8，9，12，24，36。|
|ChargeType|String|否|否|实例的计费方法。PostPaid：现收现付，PrePaid：预付。|可用值:：PostPaid，PrePaid。|

## 返回值 {#section_lh5_9o4_jcr .section}

**Fn::GetAtt**

-   OrderId：创建 MongoDB 实例的订单 ID。
-   DBInstanceId：MongoDB 实例 ID，全局唯一。
-   DBInstanceStatus：MongoDB 实例的状态信息。
-   ConnectionURI: 连接URI。
-   ReplicaSetName: 副本集名称。

## 示例 {#section_pny_5ta_ggh .section}

``` {#codeblock_zbv_fjq_uo2 .language-json}
{
  "ROSTemplateFormatVersion": "2015-09-01",
  "Resources": {
    "MongoDB": {
      "Type": "ALIYUN::MONGODB::Instance",
      "Properties": {
        "DBInstanceClass":"dds.mongo.mid",
        "DBInstanceStorage":"10",
        "VpcId": "vpc-25o8sqkwb",
        "VSwitchId": "vsw-25w8qld3m"
      }
    }
  },
  "Outputs": {
    "DBInstanceStatus": {
      "Description": "Status of mongodb instance.",
      "Value": {
        "Fn::GetAtt": [
          "MongoDB",
          "DBInstanceStatus"
        ]
      }
    },
    "InstanceId": {
      "Description": "The instance id of created mongodb instance.",
      "Value": {
        "Fn::GetAtt": [
          "MongoDB",
          "DBInstanceId"
        ]
      }
    }
  }
}
```

