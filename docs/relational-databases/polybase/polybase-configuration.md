---
title: "PolyBase の構成 | Microsoft Docs"
ms.custom: 
ms.date: 09/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: polybase
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80ff73c1-2861-438b-a13f-309155f3d6e1
caps.latest.revision: "17"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 07ace3fa24747619e8dbe64cbeb461175220a755
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="polybase-configuration"></a>PolyBase の構成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  PolyBase を構成するには、次の手順を実行します。  
  
## <a name="external-data-source-configuration"></a>外部データ ソースの構成  
 SQL Server から外部データ ソースへの接続を確立する必要があります。 接続の種類は、クエリ パフォーマンスに大きな影響を与えます。 たとえば、10 ギガ ビットのイーサネット リンクは、1 ギガ ビットのイーサネット リンクよりも PolyBase クエリのクエリ応答時間が短くなります。  
  
 **sp_configure**を使用して、Hadoop バージョンと Azure BLOB ストレージのどちらかに接続するように SQL Server を構成する必要があります。 PolyBase は、Hortonworks Data Platform (HDP) と Cloudera Distributed Hadoop (CDH) の 2 つの Hadoop ディストリビューションをサポートしています。  サポートされている外部データ ソースの一覧については、「[PolyBase Connectivity Configuration &#40;Transact-SQL&#41; (PolyBase 接続性構成 &#40;Transact-SQL&#41;)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)」を参照してください。  
1 注意: PolyBase は Cloudera 暗号化ゾーンをサポートしていません。 
  
### <a name="run-spconfigure"></a>sp_configure の実行  
  
1.  sp_configure 'hadoop connectivity' を実行し、適切な値を設定します。  値を見つけるには、「[PolyBase Connectivity Configuration &#40;Transact-SQL&#41; (PolyBase 接続性構成 &#40;Transact-SQL&#41;)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)」を参照してください。  
  
    ```sql  
    -- Values map to various external data sources.  
    -- Example: value 7 stands for Azure blob storage and Hortonworks HDP 2.3 on Linux.  
    sp_configure @configname = 'hadoop connectivity', @configvalue = 7;   
    GO   
  
    RECONFIGURE   
    GO   
    ```  
  
2.  **services.msc**を使用して SQL Server を再起動する必要があります。 SQL Server を再起動すると、次のサービスが再起動します。  
  
    -   SQL Server PolyBase Data Movement Service  
  
    -   SQL Server PolyBase エンジン  
  
## <a name="pushdown-configuration"></a>プッシュダウンの構成  
 クエリ パフォーマンスを高めるには、Hadoop クラスターへのプッシュダウン計算を有効にします。お使いの Hadoop 環境に固有の構成パラメーターを SQL Server でいくつか指定する必要があります。  
  
1.  SQL Server のインストール パスで **yarn-site.xml** というファイルを検索します。 通常、このパスは次のとおりです。  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf  
    ```  
  
2.  Hadoop コンピューターで、Hadoop 構成ディレクトリ内の対応するファイルを検索します。 このファイル内の構成キー yarn.application.classpath の値をコピーします。  
  
3.  SQL Server コンピューターで、 **yarn.site.xml ファイル** 内の **yarn.application.classpath** プロパティを検索します。 Hadoop コンピューターからこの値要素に値を貼り付けます。  

4. すべての CDH 5.X バージョンで、**yarn.site.xml file** の最後か **mapred-site.xml file** に **mapreduce.application.classpath** 構成パラメーターを追加する必要があります。 HortonWorks では、**yarn.application.classpath** 構成内にこれらの構成が含まれます。

## <a name="connecting-to-hadoop-cluster-with-hadooprpcprotection-setting"></a>Hadoop.RPC.Protection 設定での Hadoop クラスターへの接続
Hadoop クラスターで通信を保護する一般的な方法は、hadoop.rpc.protection 構成を "Privacy" または "Integrity" に変更することです。 既定では、PolyBase は構成が "Authenticate" に設定されているものと想定します。 この既定値をオーバーライドするには、次のプロパティを core-site.xml ファイルに追加する必要があります。 この構成を変更すると、Hadoop ノード間の安全なデータ転送だけでなく、SQL Server への SSL 接続も有効になります。

```
<!-- RPC Encryption information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG -->
  <property>
    <name>hadoop.rpc.protection</name>
    <value></value>
  </property> 
```




## <a name="example-yarn-sitexml-and-mapred-sitexml-files-for-cdh-5x-cluster"></a>CDH 5.X クラスターの yarn-site.xml ファイルと mapred-site.xml ファイルの例。



yarn.application.classpath と mapreduce.application.classpath で構成される Yarn-site.xml。
```
<?xml version="1.0" encoding="utf-8"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!-- Put site-specific property overrides in this file. -->
 <configuration>
  <property>
     <name>yarn.resourcemanager.connect.max-wait.ms</name>
     <value>40000</value>
  </property>
  <property>
     <name>yarn.resourcemanager.connect.retry-interval.ms</name>
     <value>30000</value>
  </property>
<!-- Applications' Configuration-->
  <property>
    <description>CLASSPATH for YARN applications. A comma-separated list of CLASSPATH entries</description>
     <!-- Please set this value to the correct yarn.application.classpath that matches your server side configuration -->
     <!-- For example: $HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/share/hadoop/common/*,$HADOOP_COMMON_HOME/share/hadoop/common/lib/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/lib/*,$HADOOP_YARN_HOME/share/hadoop/yarn/*,$HADOOP_YARN_HOME/share/hadoop/yarn/lib/* -->
     <name>yarn.application.classpath</name>
     <value>$HADOOP_CLIENT_CONF_DIR,$HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/*,$HADOOP_COMMON_HOME/lib/*,$HADOOP_HDFS_HOME/*,$HADOOP_HDFS_HOME/lib/*,$HADOOP_YARN_HOME/*,$HADOOP_YARN_HOME/lib/,$HADOOP_MAPRED_HOME/*,$HADOOP_MAPRED_HOME/lib/*,$MR2_CLASSPATH*</value>
  </property>

<!-- kerberos security information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG
  <property>
     <name>yarn.resourcemanager.principal</name>
     <value></value>
  </property>
-->
</configuration>

```
2 つの構成設定を mapred-site.xml と yarn-site.xml に分割する場合、ファイルは次のようになります。

**yarn-site.xml**
```
<?xml version="1.0" encoding="utf-8"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!-- Put site-specific property overrides in this file. -->
 <configuration>
  <property>
     <name>yarn.resourcemanager.connect.max-wait.ms</name>
     <value>40000</value>
  </property>
  <property>
     <name>yarn.resourcemanager.connect.retry-interval.ms</name>
     <value>30000</value>
  </property>
<!-- Applications' Configuration-->
  <property>
    <description>CLASSPATH for YARN applications. A comma-separated list of CLASSPATH entries</description>
     <!-- Please set this value to the correct yarn.application.classpath that matches your server side configuration -->
     <!-- For example: $HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/share/hadoop/common/*,$HADOOP_COMMON_HOME/share/hadoop/common/lib/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/lib/*,$HADOOP_YARN_HOME/share/hadoop/yarn/*,$HADOOP_YARN_HOME/share/hadoop/yarn/lib/* -->
     <name>yarn.application.classpath</name>
     <value>$HADOOP_CLIENT_CONF_DIR,$HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/*,$HADOOP_COMMON_HOME/lib/*,$HADOOP_HDFS_HOME/*,$HADOOP_HDFS_HOME/lib/*,$HADOOP_YARN_HOME/*,$HADOOP_YARN_HOME/lib/*</value>
  </property>

<!-- kerberos security information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG
  <property>
     <name>yarn.resourcemanager.principal</name>
     <value></value>
  </property>
-->
</configuration>
```

**mapred-site.xml**

プロパティ mapreduce.application.classpath が追加されています。 CDH 5.x では、Ambari の同じ命名規則に構成値があります。

```
<?xml version="1.0"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!-- Put site-specific property overrides in this file. -->
<configuration xmlns:xi="http://www.w3.org/2001/XInclude">
  <property>
    <name>mapred.min.split.size</name>
      <value>1073741824</value>
  </property>
  <property>
    <name>mapreduce.app-submission.cross-platform</name>
    <value>true</value>
  </property>
<property>
    <name>mapreduce.application.classpath</name>
    <value>$HADOOP_MAPRED_HOME/*,$HADOOP_MAPRED_HOME/lib/*,$MR2_CLASSPATH</value>
  </property>


<!--kerberos security information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG
  <property>
    <name>mapreduce.jobhistory.principal</name>
    <value></value>
  </property>
  <property>
    <name>mapreduce.jobhistory.address</name>
    <value></value>
  </property>
-->
</configuration>
  
```
  
## <a name="kerberos-configuration"></a>Kerberos の構成  
Kerberos でセキュリティが強化されているクラスターに PolyBase が認証するとき、hadoop.rpc.protection を認証に設定する必要があります。 それにより、Hadoop ノード間のデータ通信が暗号化されません。 

 Kerberos でセキュリティ保護された Hadoop クラスターに接続します [MIT KDC を使用]。
   
  
1.  SQL Server のインストール パスで Hadoop 構成ディレクトリを検索します。 通常、このパスは次のとおりです。  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf  
    ```  
  
2.  次の表に示す構成キーの Hadoop 側の構成値を検索します (Hadoop コンピューター上の Hadoop 構成ディレクトリ内でファイルを検索します)。  
  
3.  これらの構成値を、SQL Server コンピューター上の対応するファイル内の値プロパティにコピーします。  
  
    |**#**|**構成ファイル**|**構成キー**|**操作**|  
    |------------|----------------|---------------------|----------|   
    |@shouldalert|core-site.xml|polybase.kerberos.kdchost|KDC のホスト名を指定します。 例: kerberos.your-realm.com.|  
    |2|core-site.xml|polybase.kerberos.realm|Kerberos 領域を指定します。 例: YOUR-REALM.COM|  
    |3|core-site.xml|hadoop.security.authentication|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: KERBEROS<br></br>**セキュリティに関する注意:** KERBEROS は大文字で記述する必要があります。 小文字の場合、機能しない可能性があります。|   
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: hdfs/_HOST@YOUR-REALM.COM|  
    |5|mapred-site.xml|mapreduce.jobhistory.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: mapred/_HOST@YOUR-REALM.COM|  
    |6|mapred-site.xml|mapreduce.jobhistory.address|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: 10.193.26.174:10020|  
    |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: yarn/_HOST@YOUR-REALM.COM|  
  
4.  各 Hadoop ユーザーの認証情報を指定するデータベース スコープ資格情報オブジェクトを作成します。 「 [PolyBase T-SQL オブジェクト](../../relational-databases/polybase/polybase-t-sql-objects.md)」を参照してください。  
  
## <a name="next-steps"></a>次の手順  
 [PolyBase T-SQL オブジェクト](../../relational-databases/polybase/polybase-t-sql-objects.md)  
  
 [PolyBase の概要](../../relational-databases/polybase/get-started-with-polybase.md)  
  
## <a name="see-also"></a>参照  
 [PolyBase Connectivity Configuration &#40;Transact-SQL&#41; (PolyBase 接続性構成 &#40;Transact-SQL&#41;)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)   
 [PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md)  
  
  
