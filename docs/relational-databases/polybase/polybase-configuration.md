---
title: "PolyBase の構成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80ff73c1-2861-438b-a13f-309155f3d6e1
caps.latest.revision: 17
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 12
---
# PolyBase の構成
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  PolyBase を構成するには、次の手順を実行します。  
  
## <a name="external-data-source-configuration"></a>外部データ ソースの構成  
 SQL Server から外部データ ソースへの接続を確立する必要があります。 接続の種類は、予想されるクエリ パフォーマンスに大きな影響を与えます。 たとえば、10 ギガ ビットのイーサネット リンクは、1 ギガ ビットのイーサネット リンクよりも PolyBase クエリのクエリ応答時間が短くなります。  
  
 **sp_configure** を使用して、Hadoop バージョンと Azure BLOB ストレージのどちらかに接続するように SQL Server を構成する必要があります。 PolyBase は、Hortonworks Data Platform (HDP) と Cloudera Distributed Hadoop (CDH) の 2 つの Hadoop ディストリビューションをサポートしています。  サポートされている外部データ ソースの一覧については、「[PolyBase Connectivity Configuration &#40;Transact-SQL&#41; (PolyBase 接続性構成 &#40;Transact-SQL&#41;)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)」を参照してください。  
  
### <a name="run-spconfigure"></a>sp_configure の実行  
  
1.  sp_configure 'hadoop connectivity' を実行し、適切な値を設定します。  値を見つけるには、「[PolyBase Connectivity Configuration &#40;Transact-SQL&#41; (PolyBase 接続性構成 &#40;Transact-SQL&#41;)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)」を参照してください。  
  
    ```tsql  
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
 クエリ パフォーマンスを高めるには、Hadoop クラスターへのプッシュダウン計算を有効にします。  
  
1.  SQL Server のインストール パスで **yarn-site.xml** というファイルを検索します。 通常、このパスは次のとおりです。  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf  
    ```  
  
2.  Hadoop コンピューターで、Hadoop 構成ディレクトリ内の対応するファイルを検索します。 このファイル内の構成キー yarn.application.classpath の値をコピーします。  
  
3.  SQL Server コンピューターで、 **yarn.site.xml ファイル** 内の **yarn.application.classpath** プロパティを検索します。 Hadoop コンピューターからこの値要素に値を貼り付けます。  
  
## <a name="kerberos-configuration"></a>Kerberos の構成  
 Kerberos でセキュリティ保護された Hadoop クラスターに接続します [MIT KDC を使用]。  
  
1.  SQL Server のインストール パスで Hadoop 構成ディレクトリを検索します。 通常、このパスは次のとおりです。  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf  
    ```  
  
2.  次の表に示す構成キーの Hadoop 側の構成値を検索します (Hadoop コンピューター上の Hadoop 構成ディレクトリ内でファイルを検索します)。  
  
3.  これらの構成値を、SQL Server コンピューター上の対応するファイル内の値プロパティにコピーします。  
  
    |**#**|**構成ファイル**|**構成キー**|**操作**|  
    |------------|----------------|---------------------|----------|   
    |1|core-site.xml|polybase.kerberos.kdchost|Kerberos 領域を指定します。 例: YOUR-REALM.COM|  
    |2|core-site.xml|polybase.kerberos.realm|KDC のホスト名を指定します。 例: kerberos.your-realm.com.|  
    |3|core-site.xml|hadoop.security.authentication|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: KERBEROS<br></br>**セキュリティに関する注意:** KERBEROS は大文字で記述する必要があります。 小文字の場合、機能しない可能性があります。|   
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: hdfs/_HOST@YOUR-REALM.COM|  
    |5|mapred-site.xml|mapreduce.jobhistory.address|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: mapred/_HOST@YOUR-REALM.COM|  
    |6|mapred-site.xml|mapreduce.jobhistory.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: 10.193.26.174:10020|  
    |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: yarn/_HOST@YOUR-REALM.COM|  
  
4.  各 Hadoop ユーザーの認証情報を指定するデータベース スコープ資格情報オブジェクトを作成します。 「[PolyBase T-SQL オブジェクト](../../relational-databases/polybase/polybase-t-sql-objects.md)」を参照してください。  
  
## <a name="next-steps"></a>次の手順  
 [PolyBase T-SQL オブジェクト](../../relational-databases/polybase/polybase-t-sql-objects.md)  
  
 [PolyBase の概要](../../relational-databases/polybase/get-started-with-polybase.md)  
  
## <a name="see-also"></a>参照  
 [PolyBase Connectivity Configuration &#40;Transact-SQL&#41; (PolyBase 接続性構成 &#40;Transact-SQL&#41;)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)   
 [PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md)  
  
  