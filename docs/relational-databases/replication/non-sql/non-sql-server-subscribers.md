---
title: "SQL Server 以外のサブスクライバー | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サブスクリプション [SQL Server レプリケーション], SQL Server 以外のサブスクライバー"
  - "異種データ ソース, SQL Server 以外のサブスクライバー"
  - "異種データ ソース"
  - "異種データベース レプリケーション, SQL Server 以外のサブスクライバー"
  - "SQL Server 以外のサブスクライバー, SQL Server 以外のサブスクライバーについて"
  - "異種サブスクライバー"
  - "異種サブスクライバー, 異種サブスクライバーについて"
  - "サブスクライバー [SQL Server レプリケーション], SQL Server 以外のサブスクライバー"
  - "SQL Server 以外のサブスクライバー"
ms.assetid: 831e7586-2949-4b9b-a2f3-7b0b699b23ff
caps.latest.revision: 55
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 55
---
# SQL Server 以外のサブスクライバー
  以下の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーでは、プッシュ サブスクリプションを使用することで、スナップショット パブリケーションおよびトランザクション パブリケーションにサブスクライブできます。 以下に示す 2 つのデータベースの最新バージョンでは、OLE DB プロバイダーを使用したサブスクリプションがサポートされています。  
  
 SQL Server 以外のサブスクライバーへの異種レプリケーションは推奨されません。 Oracle パブリッシングは推奨されません。 データを移動するには、変更データ キャプチャと [!INCLUDE[ssIS](../../../includes/ssis-md.md)]を使用してソリューションを作成します。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
|データベース|オペレーティング システム|プロバイダー|  
|--------------|----------------------|--------------|  
|Oracle|Oracle がサポートするすべてのプラットフォーム|Oracle OLE DB プロバイダー (Oracle によって提供されます)|  
|IBM DB2|MVS、AS400、Unix、Linux、Windows (9.x を除く)|Microsoft Host Integration Server (HIS) OLE DB プロバイダー|  
  
 Oracle および IBM DB2 へのサブスクリプションを作成する方法の詳細については、次を参照してください。 [Oracle サブスクライバー](../../../relational-databases/replication/non-sql/oracle-subscribers.md) と [IBM DB2 サブスクライバー](../../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)します。  
  
## SQL Server 以外のサブスクライバーに関する注意点  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーにレプリケートする場合は、以下の点に留意してください。  
  
### 全般的な注意点  
  
-   レプリケーションでは、テーブルとインデックス付きビューをテーブルとして [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーにパブリッシュする処理をサポートしています (インデックス付きビューは、インデックス付きビューとしてレプリケートすることはできません)。  
  
-   パブリケーションの新規作成ウィザードでパブリケーションを作成して、有効化の SQL Server 以外のサブスクライバー、パブリケーションのプロパティ] ダイアログ ボックスを使用して、サブスクリプション データベース内のすべてのオブジェクトの所有者が指定されない場合の非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サブスクライバー、一方の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サブスクライバー、パブリケーション データベース内の対応するオブジェクトの所有者に設定されます。  
  
-   パブリケーションに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サブスクライバーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーが含まれる場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サブスクライバーのサブスクリプションを作成する前に、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーに対してパブリケーションを有効化する必要があります。  
  
-   既定では、スナップショット エージェントが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーに対して生成したスクリプトには、CREATE TABLE 構文に引用符なしの識別子が使用されます。 したがって、「test」という名前でパブリッシュされたテーブルは「TEST」としてレプリケートされます。 パブリケーション データベース内のテーブルと同じ大文字と小文字を使用する、 **- QuotedIdentifier** ディストリビューション エージェントのパラメーターです。  **- QuotedIdentifier** パラメーターは、パブリッシュされたオブジェクトの名前 (テーブル、列、制約など) は、空白や予約語以外のデータベースのバージョンで使用されている語が含まれる場合にも使用する必要があります[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サブスクライバーです。 このパラメーターの詳細については、「 [Replication Distribution Agent](../../../relational-databases/replication/agents/replication-distribution-agent.md)」を参照してください。  
  
-   ディストリビューション エージェントを実行するアカウントには、OLE DB プロバイダーのインストール ディレクトリに対する読み取りアクセス権が必要です。  
  
-   既定では非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サブスクリプション データベースに対してサブスクライバーでディストリビューション エージェントの使用 [(default destination)] の値 (、 **- SubscriberDB** ディストリビューション エージェントのパラメーター)。  
  
    -   Oracle の場合、1 つのサーバーに 1 つのデータベースしか作成できないため、データベースを指定する必要はありません。  
  
    -   IBM DB2 の場合、DB2 接続文字列によってデータベースを指定します。 詳細については、次を参照してください。 [非 SQL Server サブスクライバーのサブスクリプションを作成](../../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)します。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターが 64 ビット プラットフォームで実行されている場合、該当する OLE DB プロバイダーの 64 ビット バージョンを使用する必要があります。  
  
-   レプリケーションでは、パブリッシャーおよびサブスクライバーで使用される照合順序やコード ページにかかわらず、データが Unicode 形式に変換されます。 パブリッシャーとサブスクライバーの間でレプリケートを行う場合は、互換性のある照合順序やコード ページを使用することをお勧めします。  
  
-   アーティクルをパブリケーションに追加または削除する場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーのサブスクリプションは再初期化する必要があります。  
  
-   すべての [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーでサポートされる制約は、NULL および NOT NULL のみです。 主キーの制約は一意なインデックスとしてレプリケートされます。  
  
-   NULL 値の扱いはデータベースによって異なり、空白値、空の文字列、および NULL の表示方法に影響します。 また、UNIQUE 制約が定義されている列に値を挿入する際の動作にも影響します。 たとえば、Oracle では一意な列に複数の NULL 値を挿入できますが、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では一意な列に 1 つの NULL 値しか挿入できません。  
  
     他にも注意が必要なのは、列に対して NOT NULL が定義されている場合、NULL 値、空の文字列、および空白値がどのように扱われるかという点です。 Oracle サブスクライバーでのこの問題の対処方法の詳細については、「 [Oracle Subscribers](../../../relational-databases/replication/non-sql/oracle-subscribers.md)」を参照してください。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーからサブスクリプションが削除されても、レプリケーション関連のメタデータ (トランザクション シーケンス テーブル) は削除されません。  
  
### サブスクライバー データベースの要件への準拠  
  
-   パブリッシュされたスキーマおよびデータは、サブスクライバーのデータベース要件に準拠する必要があります。 たとえば、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースの最大行サイズが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] よりも小さい場合、パブリッシュされるスキーマおよびデータがこのサイズを超えないようにする必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーにレプリケートされたテーブルには、サブスクライバーのデータベースのテーブル名前付け規則が採用されます。  
  
-   DDL は、SQL Server 以外のサブスクライバーに対してはサポートされていません。 スキーマ変更の詳細については、次を参照してください。 [パブリケーション データベースでスキーマ変更を行う](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)します。  
  
### レプリケーション機能のサポート  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] には、プッシュおよびプルの 2 種類のサブスクリプションが用意されています。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーはプッシュ サブスクリプションを使用する必要があります。このサブスクリプションでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターでディストリビューション エージェントが実行されます。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2 つのスナップショットの形式を提供しています。 ネイティブ bcp モードとキャラクター モードです。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーでは、キャラクター モードのスナップショットを使用する必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーは、即時更新サブスクリプションおよびキュー更新サブスクリプションを使用できません。また、ピア ツー ピア トポロジのノードになることもできません。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーをバックアップから自動的に初期化することはできません。  
  
## 参照  
 [異種データベース レプリケーション](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [パブリケーションのサブスクライブ](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  