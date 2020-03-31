---
title: ポリベース ハドオップ セキュリティの設定
description: 外部 Hadoop に接続するように、並列データ ウェアハウスで PolyBase を構成する方法について説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/26/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: f275c77556e8abe8932e241075b9e24e2ae5db77
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "79289680"
---
# <a name="polybase-configuration-and-security-for-hadoop"></a>PolyBase の構成と Hadoop 用のセキュリティ

この記事では、Hadoop への APS PolyBase 接続に影響を与えるさまざまな構成設定のリファレンスを提供します。 PolyBase とは何かのチュートリアルについては、「[ポリベースとは 」](configure-polybase-connectivity-to-external-data.md)を参照してください。

> [!NOTE]
> APS では、すべてのコンピューティング ノードとコントロール ノードで XML ファイルを変更する必要があります。
> 
> APS の XML ファイルを変更する場合は、特に注意してください。 タグが欠落しているか、不要な文字を使用すると、xml ファイルが無効になり、機能の usablilty が妨げられる可能性があります。
> Hadoop 構成ファイルは、次のパスにあります。  
> ```  
> C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf 
> ``` 
> xml ファイルを変更すると、サービスを再開して有効にする必要があります。

## <a name="hadooprpcprotection-setting"></a><a id="rpcprotection"></a> Hadoop.RPC.Protection 設定

Hadoop クラスターで通信を保護する一般的な方法は、hadoop.rpc.protection 構成を "Privacy" または "Integrity" に変更することです。 既定では、PolyBase は構成が "Authenticate" に設定されているものと想定します。 この既定値をオーバーライドするには、次のプロパティを core-site.xml ファイルに追加します。 この構成を変更すると、Hadoop ノード間の安全なデータ転送と、SQL Server への SSL 接続が有効になります。

```xml
<!-- RPC Encryption information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG -->
   <property>
     <name>hadoop.rpc.protection</name>
     <value></value>
   </property> 
```

## <a name="kerberos-configuration"></a><a id="kerberossettings"></a>Kerberos 構成  

PolyBase が Kerberos でセキュリティが強化されているクラスターに対して認証を行う場合、hadoop.rpc.protection が既定で "Authenticate" に設定されている必要があることに注意してください。 これにより、Hadoop ノード間のデータ通信が暗号化されなくなります。 hadoop.rpc.protection の "Privacy" または "Integrity" 設定を使用するには、PolyBase サーバーで core-site.xml ファイルを更新します。 詳細については、前のセクションの「[Hadoop.RPC.Protection 設定での Hadoop クラスターへの接続](#rpcprotection)」を参照してください。

MIT KDC を使用して Kerberos で保護された Hadoop クラスターに接続するには、すべての APS コンピューティング ノードと制御ノードで次の変更が必要です。

1. APS のインストール パスで Hadoop 構成ディレクトリを検索します。 通常、このパスは次のとおりです。  

   ```  
   C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf  
   ```  

2. 次の表に示す構成キーの Hadoop 側の構成値を検索します (Hadoop コンピューター上の Hadoop 構成ディレクトリ内でファイルを検索します)。  
   
3. これらの構成値を、SQL Server コンピューター上の対応するファイル内の値プロパティにコピーします。  
   
   |**#**|**構成ファイル**|**構成キー**|**操作**|  
   |------------|----------------|---------------------|----------|   
   |1|core-site.xml|polybase.kerberos.kdchost|KDC のホスト名を指定します。 例: kerberos.your-realm.com.|  
   |2|core-site.xml|polybase.kerberos.realm|Kerberos 領域を指定します。 例: YOUR-REALM.COM|  
   |3|core-site.xml|hadoop.security.authentication|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: KERBEROS<br></br>**セキュリティに関する注意:** KERBEROS は大文字で記述する必要があります。 小文字の場合、機能しない可能性があります。|   
   |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: hdfs/_HOST@YOUR-REALM.COM|  
   |5|mapred-site.xml|mapreduce.jobhistory.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: mapred/_HOST@YOUR-REALM.COM|  
   |6|mapred-site.xml|mapreduce.jobhistory.address|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: 10.193.26.174:10020|  
   |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: yarn/_HOST@YOUR-REALM.COM|  

**core-site.xml**
```xml
<property>
  <name>polybase.kerberos.realm</name>
  <value></value>
</property>
<property>
  <name>polybase.kerberos.kdchost</name>
  <value></value>
</property>
<property>
    <name>hadoop.security.authentication</name>
    <value>KERBEROS</value>
</property>
```

**hdfs-site.xml**
```xml
<property>
  <name>dfs.namenode.kerberos.principal</name>
  <value></value> 
</property>
```

**mapred-site.xml**
```xml
<property>
  <name>mapreduce.jobhistory.principal</name>
  <value></value>
</property>
<property>
  <name>mapreduce.jobhistory.address</name>
  <value></value>
</property>
```

**yarn-site.xml**
```xml
<property>
  <name>yarn.resourcemanager.principal</name>
  <value></value>
</property>
```

4. 各 Hadoop ユーザーの認証情報を指定するデータベース スコープ資格情報オブジェクトを作成します。 「 [PolyBase T-SQL オブジェクト](../relational-databases/polybase/polybase-t-sql-objects.md)」を参照してください。

## <a name="hadoop-encryption-zone-setup"></a><a id="encryptionzone"></a>Hadoop 暗号化ゾーンのセットアップ
Hadoop 暗号化ゾーンを使用している場合は、次のようにコア サイト.xml と hdfs-site.xml を変更します。 KMS サービスが実行されている IP アドレスを、対応するポート番号で指定します。 CDH 上の KMS のデフォルトポートは 16000 です。

**core-site.xml**
```xml
<property>
  <name>hadoop.security.key.provider.path</name>
  <value>kms://http@<ip address>:16000/kms</value> 
</property>
```

**hdfs-site.xml**
```xml
<property>
  <name>dfs.encryption.key.provider.uri</name>
  <value>kms://http@<ip address>:16000/kms</value>
</property>
<property>
  <name>hadoop.security.key.provider.path</name>
  <value>kms://http@<ip address>:16000/kms</value>
  </property>
```