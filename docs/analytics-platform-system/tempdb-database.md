---
title: "tempdb データベース (SQL Server PDW)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5840033d-2dc6-4576-8a5f-067e2a58b170
caps.latest.revision: "22"
ms.workload: not set
ms.openlocfilehash: 459265906774604f4d98f7cfb2bd2ad09485cc7e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="tempdb-database"></a>tempdb データベース
**tempdb**はユーザー データベースのローカル一時テーブルを格納する SQL Server PDW システム データベースです。 一時テーブルは、クエリのパフォーマンスを向上させるためによく使用されます。 たとえば、一時テーブルを使用して、スクリプトをモジュール化でき、計算されたデータを再利用できます。  
  
システム データベースの詳細については、次を参照してください。[システム データベース](system-databases.md)です。  
  
## <a name="Basics"></a>主な用語と概念  
*ローカル一時テーブル*  
A*ローカル一時テーブル*をローカル ユーザーのセッションが作成された一時テーブルであり、テーブル名の前に # プレフィックスを使用します。 各セッションでは、独自のセッションのローカル一時テーブルのデータにのみアクセスできます。  
  
各セッションは、すべてのセッションでローカル一時テーブルのメタデータを表示できます。 たとえば、すべてのセッションがのすべてのローカル一時テーブルのメタデータを表示できます、`SELECT * FROM tempdb.sys.tables`クエリ。  
  
グローバル一時テーブル  
*グローバル一時テーブル*、SQL Server でサポートされている、## の構文は、SQL Server PDW のこのリリースではサポートされていません。  
  
pdwtempdb  
**pdwtempdb**はローカル一時テーブルを格納するデータベースです。  
  
PDW は、SQL Server を使用して、一時テーブルを実装しません**tempdb**データベース。 代わりに、PDW データベースに保存、pdwtempdb と呼ばれます。 このデータベースは、各計算ノードに存在し、PDW インターフェイスを通じてユーザーには表示されません。 管理者コンソールで、[ストレージ] ページが表示されますこれらを占めてのという名前の PDW システム データベースで**tempdb sql**です。  
  
tempdb  
**tempdb**は、SQL Server tempdb データベース。 最小ログ記録を使用します。 SQL Server では、コンピューティング ノードで tempdb を使用して、SQL Server 操作を実行する過程で必要な一時テーブルを格納します。  
  
SQL Server PDW からテーブルを削除する**tempdb**とき。  
  
-   DROP TABLE ステートメントが実行されます。  
  
-   セッションは切断されます。 セッションの一時テーブルだけが削除されます。  
  
-   アプライアンスは、シャット ダウンします。  
  
-   コントロールのノードには、クラスターのフェールオーバーがあります。  
  
## <a name="general-remarks"></a>全般的な解説  
SQL Server PDW は、特に明示しない限り、一時テーブルと永続的なテーブルに対して同じ操作を実行します。 たとえば、パーマネント テーブルと同じように、ローカル一時テーブル内のデータが分散またはコンピューティング ノード間でレプリケートします。  
  
## <a name="LimitationsRestrictions"></a>制限事項と制約事項  
制限事項と制約 SQL Server PDW**tempdb**データベース。 *ことはできません。*  
  
-   始まり、グローバル一時テーブルを作成する ## します。  
  
-   バックアップまたは復元の実行**tempdb**です。  
  
-   アクセス許可を変更**tempdb**で、 **GRANT**、 **DENY**、または**取り消す**ステートメントです。  
  
-   実行**DBCC SHRINKLOG**の**tempdb**tempdb です。  
  
-   DDL 操作の実行**tempdb**です。 これにはいくつかの例外があります。 詳細については、ローカル一時テーブル上の制限事項と制約事項の次の一覧を参照してください。  
  
制限事項とローカル一時テーブルに制約します。 *ことはできません。*  
  
-   一時テーブル名の変更します。  
  
-   一時テーブルでは、パーティション、ビュー、または非クラスター化インデックスを作成します。 **ALTER INDEX**いずれかで作成されたテーブルのクラスター化インデックスを再構築するために使用できます。  
  
-   許可、拒否、一時テーブルへのアクセス許可を変更するか、ステートメントを取り消します。  
  
-   一時テーブル上でデータベース コンソール コマンドを実行します。  
  
-   同じバッチ内の 2 つ以上の一時テーブルに同じ名前を使用します。 バッチ内で 1 つ以上のローカル一時テーブルを使用した場合、一意の名前でそれぞれ必要があります。 複数のセッションは同じバッチを実行して、同じローカル一時テーブルを作成する場合、SQL Server PDW は内部的に各ローカル一時テーブルの一意の名前を維持するためにローカル一時テーブル名に数値サフィックスを追加します。  
  
> [!NOTE]  
> *できます*を作成し、一時テーブルで統計を更新します**。ALTER INDEX**をクラスター化インデックスを再構築するために使用できます。  
  
## <a name="permissions"></a>アクセス許可  
すべてのユーザーが tempdb 内に一時オブジェクトを作成できます。 ユーザーは追加の権限を付与されない限り、自分で作成したオブジェクトにしかアクセスできません。 ユーザーが tempdb を使用できないように tempdb への接続権限を取り消すことはできますが、一部のルーチン処理で tempdb を使用する必要があるためお勧めしません。  
  
## <a name="RelatedTasks"></a>関連タスク  
  
|処理手順|Description|  
|---------|---------------|  
|内のテーブルを作成する**tempdb**です。|CREATE TABLE と CREATE TABLE AS SELECT ステートメントを使用して、ユーザーの一時テーブルを作成できます。 詳細については、次を参照してください。 [CREATE TABLE](../t-sql/statements/create-table-azure-sql-data-warehouse.md)と[CREATE TABLE AS SELECT](../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)です。|  
|既存のテーブルの一覧を表示**tempdb**です。|`SELECT * FROM tempdb.sys.tables;`|  
|既存の列の一覧を表示**tempdb**です。|`SELECT * FROM tempdb.sys.columns;`|  
|既存のオブジェクトの一覧を表示**tempdb**です。|`SELECT * FROM tempdb.sys.objects;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
