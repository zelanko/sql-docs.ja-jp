---
title: "SQL Database へのレプリケーション | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Database のレプリケーション"
  - "レプリケーション, SQL Database"
ms.assetid: e8484da7-495f-4dac-b38e-bcdc4691f9fa
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# SQL Database へのレプリケーション
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションを構成できます [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]します。  
  
 **サポートされている構成:**  
  
-    [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスであることができます [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部設置型のインスタンスを実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、クラウドでの Azure の仮想マシンで実行します。 詳細については、「 [Azure Virtual Machines 上の SQL Server の概要](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/)」を参照してください。  
  
-   [!INCLUDE[ssSDS](../../includes/sssds-md.md)] は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーのプッシュ サブスクライバーである必要があります。  
  
-   ディストリビューション データベースとレプリケーション エージェントは、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]には配置できません。  
  
-   スナップショットおよび一方向トランザクション レプリケーションがサポートされています。 ピアツーピア トランザクション レプリケーションおよびマージ レプリケーションはサポートされていません。  
  
## バージョン  
 パブリッシャーとディストリビューターは、次のいずれかのバージョンである必要があります。  
  
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP1 CU3  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] RTM CU10  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 CU8  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP3  
  
 古いバージョンを使用してレプリケーションを構成しようとしてエラーを起こす番号 (プロセスはサブスクライバーに接続できませんでした) MSSQL_REPL20084 および MSSQL_REPL40532 (サーバーを開くことができません \< 名前> ログインで要求します。 ログインに失敗しました。) が表示される場合があります。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] のサブスクライバーは任意のリージョンに存在する V12 以上である必要があります。  
  
 すべての機能を使用する [!INCLUDE[ssSDS](../../includes/sssds-md.md)] の最新バージョンを使用する必要があります [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx) と [SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx)します。  
  
## 解説  
 レプリケーションは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、またはパブリッシャーで [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行して構成できます。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ポータルを使用してレプリケーションを構成することはできません。  
  
 レプリケーションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続に [!INCLUDE[ssSDS](../../includes/sssds-md.md)]認証ログインのみを使用できます。  
  
 レプリケートしたテーブルには、主キーが必要です。  
  
 既存の Azure サブスクリプションと、既存の [!INCLUDE[ssSDS](../../includes/sssds-md.md)] V12 が必要です。  
  
 上の単一のパブリケーション [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 両方をサポートできます [!INCLUDE[ssSDS](../../includes/sssds-md.md)] と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (内部設置型と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure の仮想マシンで) サブスクライバーです。  
  
 レプリケーションの管理、監視、および内部設置型からのトラブルシューティングを実行する必要があります [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] へは、プッシュ サブスクリプションのみがサポートされています。  
  
 のみ `@subscriber_type = 0` ではサポートされて **sp_addsubscription** SQL データベースにします。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 双方向、イミディ エイト、更新可能なまたはピア ツー ピア レプリケーションはサポートされません。  
  
## レプリケーションのアーキテクチャ  
 ![replication-to-sql-database](../../relational-databases/replication/media/replication-to-sql-database.png "replication-to-sql-database")  
  
## シナリオ  
  
#### 典型的なレプリケーションのシナリオ  
  
1.  内部設置型のトランザクション レプリケーションのパブリケーションを作成する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースです。  
  
2.  内部設置型の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、 **サブスクリプション新規作成ウィザード** または [!INCLUDE[tsql](../../includes/tsql-md.md)] へのサブスクリプションへのプッシュを作成するステートメント [!INCLUDE[ssSDS](../../includes/sssds-md.md)]します。  
  
3.  初期データセットは、通常、スナップショット エージェントにより作成され、ディストリビューション エージェントにより配信および適用されるスナップショットです。 初期のデータ セットできますも経由で提供される、バックアップまたはその他の手段など [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]します。  
  
#### データの移行シナリオ  
  
1.  トランザクション レプリケーションを使用して内部設置型からデータを複製 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースを [!INCLUDE[ssSDS](../../includes/sssds-md.md)]します。  
  
2.  更新をクライアントまたは中間層アプリケーションのリダイレクト、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] コピーします。  
  
3.  テーブルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンの更新を停止し、パブリケーションを削除します。  
  
## 制限事項  
 次のオプションは、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] のサブスクリプションではサポートされていません。  
  
-   ファイル グループの関連付けのコピー  
  
-   テーブルのパーティション分割スキーマのコピー  
  
-   インデックスのパーティション分割のスキーマのコピー  
  
-   ユーザー定義の統計情報のコピー  
  
-   既定のバインドのコピー  
  
-   ルールのバインドのコピー  
  
-   フルテキスト インデックスのコピー  
  
-   XML XSD のコピー  
  
-   XML インデックスのコピー  
  
-   アクセス許可のコピー  
  
-   空間インデックスのコピー  
  
-   フィルター選択されたインデックスのコピー  
  
-   データ圧縮属性のコピー  
  
-   スパース列属性のコピー  
  
-   filestream の MAX データ型への変換  
  
-   hierarchyid の MAX データ型への変換  
  
-   空間の MAX データ型への変換  
  
-   拡張プロパティのコピー  
  
-   アクセス許可のコピー  
  
 未定の制限:  
  
-   コピーの照合順序  
  
-   [SP のシリアル化されたトランザクションでの実行]  
  
## 使用例  
 パブリケーションおよびプッシュ サブスクリプションを作成します。 詳細については、以下をご覧ください。  
  
-   [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)  
  
-   [プッシュ サブスクリプションを作成](../../relational-databases/replication/create-a-push-subscription.md) を使用して、 [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] サブスクライバーとして論理サーバー名 (たとえば **N'azuresqldbdns.database.windows.net'**) および [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 転送先データベース名 (たとえば **AdventureWorks**)。  
  
## 参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [レプリケーションの種類](../../relational-databases/replication/types-of-replication.md)   
 [監視と #40 です。レプリケーションと #41 です。](../../relational-databases/replication/monitor/monitoring-replication.md)   
 [サブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription.md)  
  
  