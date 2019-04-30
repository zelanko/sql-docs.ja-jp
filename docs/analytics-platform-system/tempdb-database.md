---
title: Tempdb データベースの Parallel Data Warehouse |Microsoft Docs
description: Parallel Data Warehouse での Tempdb データベース。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 7e11f4eff980358f4b4906f8a100cfc509d19dd5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63156963"
---
# <a name="tempdb-database-in-parallel-data-warehouse"></a>Parallel Data Warehouse での tempdb データベース
**tempdb**はユーザー データベースのローカル一時テーブルを格納する SQL Server PDW システム データベースです。 一時テーブルは、クエリのパフォーマンスを向上させるためによく使用されます。 たとえば、一時テーブルを使用して、スクリプトをモジュール化でき、計算されたデータを再利用できます。  
  
システム データベースの詳細については、次を参照してください。[システム データベース](system-databases.md)します。  
  
## <a name="Basics"></a>主な用語と概念  
*ローカル一時テーブル*  
A*ローカル一時テーブル*ローカル ユーザーのセッションで作成した一時テーブルであり、テーブル名の前に # プレフィックスが使用されます。 各セッションでは、独自のセッションのローカル一時テーブル内のデータのみアクセスできます。  
  
各セッションでは、すべてのセッションで、ローカル一時テーブルのメタデータを表示できます。 すべてのセッションがのすべてのローカル一時テーブルのメタデータを表示するなど、`SELECT * FROM tempdb.sys.tables`クエリ。  
  
グローバル一時テーブル  
*グローバル一時テーブル*、SQL Server でサポートされている、## の構文は、SQL Server PDW のこのリリースではサポートされていません。  
  
pdwtempdb  
**pdwtempdb**はローカル一時テーブルを格納するデータベースです。  
  
PDW は、SQL Server を使用して一時テーブルを実装していません**tempdb**データベース。 代わりに、PDW データベースに格納する pdwtempdb と呼ばれます。 このデータベースは、各コンピューティング ノードに存在し、PDW インターフェイスを介してユーザーには表示されません。 [ストレージ] ページで、管理コンソールでに表示されるこれらを占めての PDW システム データベースと呼ばれる**tempdb sql**します。  
  
tempdb  
**tempdb**は、SQL Server tempdb データベースです。 最小ログ記録を使用します。 SQL Server では、SQL Server の操作を実行する過程で必要な一時テーブルを保存するのにコンピューティング ノードで tempdb を使用します。  
  
SQL Server PDW からテーブルを削除する**tempdb**とき。  
  
-   DROP TABLE ステートメントが実行されます。  
  
-   セッションは切断されます。 セッションの一時テーブルのみが削除されます。  
  
-   アプライアンスは、シャット ダウンします。  
  
-   コントロールのノードには、クラスターのフェイル オーバーがあります。  
  
## <a name="general-remarks"></a>全般的な解説  
SQL Server PDW は、明示的に特に明記しない限り、一時テーブルと永続的なテーブルに対して同じ操作を実行します。 たとえば、パーマネント テーブルと同様、ローカル一時テーブル内のデータが分散またはコンピューティング ノード間でレプリケートします。  
  
## <a name="LimitationsRestrictions"></a>制限事項と制約事項  
制限事項と制約 SQL Server の PDW**tempdb**データベース。 *ことはできません。*  
  
-   始まるグローバル一時テーブルを作成する ## します。  
  
-   バックアップまたは復元の実行**tempdb**します。  
  
-   アクセス許可を変更**tempdb**で、 **GRANT**、 **DENY**、または**取り消す**ステートメント。  
  
-   実行**DBCC SHRINKLOG**の**tempdb**tempdb です。  
  
-   DDL 操作を実行**tempdb**します。 これにはいくつかの例外があります。 詳細については、ローカル一時テーブル上の制限事項と制約事項の次の一覧を参照してください。  
  
制限事項とローカル一時テーブル上の制約。 *ことはできません。*  
  
-   一時テーブル名の変更します。  
  
-   一時テーブルでは、パーティション、ビュー、または非クラスター化インデックスを作成します。 **ALTER INDEX**いずれかで作成されたテーブルのクラスター化インデックスを再構築するために使用できます。  
  
-   GRANT、DENY、一時テーブルにアクセス許可を変更または REVOKE ステートメント。  
  
-   一時テーブルでは、データベース コンソール コマンドを実行します。  
  
-   同じバッチ内の 2 つ以上の一時テーブルに同じ名前を使用します。 バッチ内で複数のローカル一時テーブルを使用する場合、各テーブルの名前は一意でなければなりません。 複数のセッションは同じバッチを実行して、同じローカル一時テーブルを作成する場合、SQL Server PDW は内部的に各ローカル一時テーブルの一意の名前を維持するためにローカル一時テーブル名に数値サフィックスを追加します。  
  
> [!NOTE]  
> *できます*を作成し、一時テーブルで統計を更新します **。ALTER INDEX**クラスター化インデックスを再構築するために使用できます。  
  
## <a name="permissions"></a>アクセス許可  
すべてのユーザーが tempdb 内に一時オブジェクトを作成できます。 ユーザーは追加の権限を付与されない限り、自分で作成したオブジェクトにしかアクセスできません。 ユーザーが tempdb を使用できないように tempdb への接続権限を取り消すことはできますが、一部のルーチン処理で tempdb を使用する必要があるためお勧めしません。  
  
## <a name="RelatedTasks"></a>関連するタスク  
  
|処理手順|説明|  
|---------|---------------|  
|内のテーブルを作成する**tempdb**します。|CREATE TABLE と CREATE TABLE AS SELECT ステートメントを使用して、ユーザーの一時テーブルを作成できます。 詳細については、次を参照してください。 [CREATE TABLE](../t-sql/statements/create-table-azure-sql-data-warehouse.md)と[CREATE TABLE AS SELECT](../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)します。|  
|既存のテーブルの一覧を表示**tempdb**します。|`SELECT * FROM tempdb.sys.tables;`|  
|既存の列の一覧を表示**tempdb**します。|`SELECT * FROM tempdb.sys.columns;`|  
|既存のオブジェクトの一覧を表示**tempdb**します。|`SELECT * FROM tempdb.sys.objects;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
