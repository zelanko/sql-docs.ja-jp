---
title: "外部データ (Analytics Platform System) への接続を PolyBase を構成します。"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6f14ac21-a086-4c05-861f-0a12bf278259
caps.latest.revision: 
ms.openlocfilehash: d9777fb2bbfd9af2598a422fc072877ff0b78959
ms.sourcegitcommit: c77a8ac1ab372927c09bf241d486e96881b61ac9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="configure-polybase-connectivity-to-external-data"></a>外部データへの接続を PolyBase を構成します。
外部 Hadoop または Microsoft Azure ストレージ blob のデータ ソースへの接続に SQL Server PDW で PolyBase を構成する方法について説明します。 PolyBase を使用して、Hadoop や Azure blob ストレージ、SQL Server PDW など、複数のソースからデータを統合するクエリを実行します。  
  
### <a name="to-configure-connectivity"></a>接続を構成するには  
  
1.  Sqlcmd または SQL Server Data Tools (SSDT) などのクエリ ツールを開き、sp_configure 'hadoop connectivity' の現在の設定を表示するを実行します。  
  
    ![hadoop 接続設定](./media/configure-polybase-connectivity-to-external-data/APS_PDW_sp_configure.png "APS_PDW_sp_configure")  
  
2.  どの Hadoop 接続を設定する必要性と現在の設定を変更する必要があるかどうかを決定します。 このオプションは、SQL Server PDW 地域全体に適用されます。 構成設定とバージョンの一覧については、次を参照してください。 [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)です。  
  
3.  'Hadoop connectivity' の設定を変更するには、RECONFIGURE で sp_configure を実行します。 いくつかの例のとおりです。  
  
    ```sql  
    --Enable connectivity to Hortonworks Data Platform for Windows Server (HDP), HDInsight on Analytics Platform System, or HDInsight’s Microsoft Azure blob storage  
    EXEC sp_configure 'hadoop connectivity', 4;   
    RECONFIGURE;  
  
    -- Enable connectivity to Hortonworks Data Platform (HDP)for Linux   
    EXEC sp_configure 'hadoop connectivity', 5;   
    RECONFIGURE;  
  
    -- Enable connectivity to Cloudera CDH for Linux   
    EXEC sp_configure 'hadoop connectivity', 3;   
    RECONFIGURE;  
  
    -- Disable the Hadoop connectivity option   
    EXEC sp_configure 'hadoop connectivity', 0;  
    RECONFIGURE;  
    ```  
  
    RECONFIGURE を実行中の sp_configure では、構成値を設定します。 実行値を設定する領域の再起動が必要です。 再起動が必要なため、[次へ] の停止後も、次の手順は、core-site.xml の変更後までに再起動を行う必要はありません。  
  
4.  外部データ ソースとして Microsoft Azure blob ストレージを有効にするには、PDW core-site.xml ファイルに 1 つまたは複数の Microsoft Azure ストレージ アカウント アクセス キーを追加します。 キーを追加します。  
  
    1.  Microsoft Azure ストレージ アカウント名を検索します。 をストレージ アカウントへのログインを表示する、[Azure ポータル](https://portal.azure.com) をクリック**ストレージ アカウント (クラシック)**です。  
  
        ![Windows Azure ストレージ アカウント名](./media/configure-polybase-connectivity-to-external-data/APS_PDW_AzureStorageAccountName.png "APS_PDW_AzureStorageAccountName")  
  
    2.  Azure ストレージ アカウント アクセス キーを検索します。 これを行うには、ストレージ アカウント名をクリックし、設定 ブレード をクリックして**キー**です。 これは、アカウント名とストレージ キーを示します。  
  
        ![Windows Azure ストレージ アカウント アクセス キー](./media/configure-polybase-connectivity-to-external-data/APS_PDW_AzureStorageAccountAccessKey.png "APS_PDW_AzureStorageAccountAccessKey")  
  
    3.  PDW 管理ノードにリモート デスクトップ接続を開きます。  
  
    4.  C:\Program files \microsoft SQL Server 並列データ Warehouse\100\Hadoop\conf\core-site.xml ファイルを開きます。  
  
    5.  Core-site.xml に名前と値の属性を持つ次のプロパティを追加します。  
  
        ```xml  
        <property>  
          <name>fs.azure.account.key.<your storage account name>.blob.core.windows.net</name>  
          <value><your storage account access key></value>  
        </property>  
        ```  
  
        この例では、前に示したアカウント名とアクセス キーを使用します。  
  
        ```xml  
        <property>  
          <name>fs.azure.account.key.CustomerX.blob.core.windows.net</name>  
          <value>yyeTfCxxxxxxxxQ5WdnapXw77W+FwzHUhX/p/f26fIpnNFGtewzyRN90e1/qmTOl1xxxxxxxxa0goG71LsNcw==</value>  
        </property>  
        ```  
  
        > [!CAUTION]  
        > セキュリティ予防措置を取って core-site.xml のアクセス キーを格納する前にします。 CONTROL SERVER または ALTER ANY EXTERNAL DATA SOURCE のアクセス許可を持つすべてのユーザーには、このアカウントにアクセスする外部データ ソースを作成できます。 外部データ ソースが作成されると、CREATE TABLE 権限を持つすべての SQL Server PDW ユーザーはこのストレージ アカウントにアクセスする外部テーブルを作成できます。 ユーザーは、アカウントのデータにアクセスし、アカウント内のリソースを消費します。  
  
    6.  Core-site.xml に変更を保存します。  
  
5.  Yarn.application.classpath プロパティと値を yarn-site.xml ファイルを追加します。  
  
    外部の Hadoop 1.3 に接続している場合は、この手順をスキップします。  
  
    Hadoop 2.0 から始まり、yarn-site.xml ファイルには、Hadoop YARN フレームワークの構成設定が含まれています。 このファイルは、[管理] ノードの下にあるは**C:\program files \microsoft SQL Server 並列データ Warehouse\100\Hadoop\conf\\**です。  
  
    Windows または Linux で、外部の Hadoop 2.0 クラスターに対して PolyBase クエリを実行するには、yarn.application.classpath プロパティと、外部の Hadoop クラスター上の yarn-site.xml 設定と一致するように値を構成する必要があります。 外部の Hadoop クラスターは、既定の設定を使用する場合でも、この構成は必要があります。  
  
    既定の設定例:  
  
    ```xml  
    <property>  
        <name>yarn.application.classpath</name>  
        <value>  
          %HADOOP_CONF_DIR%,  
          %HADOOP_COMMON_HOME%/share/hadoop/common/*,  
          %HADOOP_COMMON_HOME%/share/hadoop/common/lib/*,  
          %HADOOP_HDFS_HOME%/share/hadoop/hdfs/*,  
          %HADOOP_HDFS_HOME%/share/hadoop/hdfs/lib/*,  
          %HADOOP_YARN_HOME%/share/hadoop/yarn/*,  
          %HADOOP_YARN_HOME%/share/hadoop/yarn/lib/*  
         </value>  
      </property>  
    ```  
  
    Yarn-site.xml で任意のプロパティを定義すると、PolyBase は、HDInsight リージョンに対してクエリを実行するときにそれらのプロパティ設定を使用します。 Windows 上の HDInsight リージョンと外部の Hadoop 2.0 クラスターの両方に対して PolyBase クエリを実行する場合は、すべての yarn-site.xml ファイル間で一貫性がある必要がありますか、PolyBase クエリは失敗します。  
  
    HDInsight リージョンと外部の Hadoop 2.0 クラスターの両方に対して、PolyBase を実行するには、外部の Hadoop クラスターで yarn-site.xml 既定の設定を使用します。  
  
6.  PDW 地域を再起動します。 これを行うには、Configuration Manager ツールを使用します。 参照してください[構成マネージャー &#40; を起動Analytics Platform System &#41;](launch-the-configuration-manager.md).  
  
7.  Hadoop 接続のセキュリティ設定を確認します。 場合、**弱い認証**側を使用して有効になって Hadoop `dfs.permission = true`、Hadoop ユーザーを作成する必要があります**pdw_user**すべて読み取りを許可し、このユーザーに書き込みアクセス許可。 SQL Server PDW と SQL Server PDW から対応する呼び出しとして常に発行**pdw_user**です。  これは、固定ユーザー名であり、このバージョンの Hadoop 接続および SQL Server PDW のリリースでは変更できません。 使用して Hadoop のセキュリティが無効になっている場合`dfs.permission = false`、それ以上の操作を実行する必要はありません。  
  
8.  Microsoft Azure blob ストレージに外部データ ソースを作成できるユーザーを決定します。 これらのユーザーの各ストレージ アカウント名を指定しても**ALTER ANY EXTERNAL DATA SOURCE**または**CONTROL SERVER**権限です。  
  
9. Hadoop 接続の場合は、Hadoop に外部データ ソースを作成できるユーザーを決定します。 これらのユーザーの個々 の各 Hadoop 名前ノードの IP アドレスとポート番号を付与し、付与**ALTER ANY EXTERNAL DATA SOURCE**または**CONTROL SERVER**権限です。  
  
10. WASB に接続すると、DNS 転送アプライアンスでの構成も必要です。 DNS の転送を構成するのを参照してください[非アプライアンス DNS 名を解決する &#40; を DNS フォワーダーを使用。Analytics Platform System &#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
承認されたユーザーには、外部データ ソース、外部ファイル形式、および外部テーブルを作成できますようになりました。 これらを使用するとして Hadoop, を含む複数のソースからデータを統合するが、Microsoft Azure blob ストレージ、および SQL Server PDW です。  

## <a name="kerberos-configuration"></a>Kerberos の構成  
Kerberos のセキュリティで保護されたクラスターに PolyBase が認証されると、ときに、hadoop.rpc.protection 設定する必要がありますに設定することの認証に注意してください。 これにより、データ通信が暗号化されていない Hadoop ノード間で残ります。 

 [Using MIT KDC] Kerberos でセキュリティ保護された Hadoop クラスターに接続します。
   
  
1.  [管理] ノードでのインストール パスで Hadoop 構成ディレクトリを検索します。  
  
    ```  
    C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf
    ```  
  
2.  次の表に示す構成キーの Hadoop 側の構成値を検索します (Hadoop コンピューター上の Hadoop 構成ディレクトリ内でファイルを検索します)。  
  
3.  コントロールのノード上の対応するファイル内の値プロパティに、構成値をコピーします。  
  
    |**#**|**構成ファイル**|**構成キー**|**操作**|  
    |------------|----------------|---------------------|----------|   
    |1|core-site.xml|polybase.kerberos.kdchost|KDC のホスト名を指定します。 例: kerberos.your-realm.com.|  
    |2|core-site.xml|polybase.kerberos.realm|Kerberos 領域を指定します。 例: YOUR-REALM.COM|  
    |3|core-site.xml|hadoop.security.authentication|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: KERBEROS<br></br>**セキュリティに関する注意:** KERBEROS は大文字で記述する必要があります。 小文字の場合、機能しない可能性があります。|   
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: hdfs/_HOST@YOUR-REALM.COM|  
    |5|mapred-site.xml|mapreduce.jobhistory.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: mapred/_HOST@YOUR-REALM.COM|  
    |6|mapred-site.xml|mapreduce.jobhistory.address|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: 10.193.26.174:10020|  
    |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: yarn/_HOST@YOUR-REALM.COM|  
  
4. 各 Hadoop ユーザーの認証情報を指定するデータベース スコープ資格情報オブジェクトを作成します。 「 [PolyBase T-SQL オブジェクト](../relational-databases/polybase/polybase-t-sql-objects.md)」を参照してください。  

5. PDW 地域を再起動します。 これを行うには、Configuration Manager ツールを使用します。 参照してください[構成マネージャー &#40; を起動Analytics Platform System &#41;](launch-the-configuration-manager.md).
 
## <a name="see-also"></a>参照  
[アプライアンスの構成 &#40;です。Analytics Platform System &#41;](appliance-configuration.md)  
<!-- MISSING LINKS [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  -->  
  
