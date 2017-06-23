---
title: "更新済み - リレーショナル データベースのドキュメント |Microsoft ドキュメント"
description: "最近変更したドキュメントについては、リレーショナル データベースの更新されたコンテンツのスニペットを表示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: relational-databases
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 05/23/2017
ms.author: genemi
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: 3ab051a6fd00670139bb1089dcd3f4af76b9ecef
ms.contentlocale: ja-jp
ms.lasthandoff: 06/23/2017

---
# <a name="new-and-recently-updated-relational-databases-docs"></a>新規または最近の更新: リレーショナル データベース ドキュメント



ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 場合によっては抜粋を付けること不完全な書式設定、マークダウンとしてソース アーティクルからです。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- *更新プログラムの日付範囲:* &nbsp; **2017 年-05-01** &nbsp;対&nbsp; **2017 年-05-23**
- *サブジェクト領域:* &nbsp; **リレーショナル データベース**です。




&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新されたアーティクルの抜粋が

このセクションでは、大幅な更新が最近発生したアーティクルから収集された更新プログラムの抜粋を表示します。

ここに表示される抜粋は、適切なセマンティック コンテキストから区切りが表示されます。 また、区切ることもあります抜粋が実際の資料の周囲にある重要なマークダウン構文からです。 したがってこれらの抜粋は、一般的なガイダンスのみです。 のみの抜粋を使用するをクリックし、実際の資料を参照してくださいに時間がかかって各自の興味を保証するかどうかを把握できます。

これらおよびその他の理由は、これらの抜粋からコードをコピーしない場合と受け取らない正確な情報源として任意のテキストの抜粋です。 代わりに、実際の資料を参照してください。



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-create-a-graph-database-and-run-some-pattern-matching-queries-using-t-sqlgraphssql-graph-samplemd"></a>1.&nbsp;[グラフ データベースを作成し、T-SQL を使用してクエリに一致するパターンを実行](graphs/sql-graph-sample.md)

*Updated: 2017-05-04* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Next](#TitleNum_2))

<!-- Source markdown line 68.  ms.author= "shkale".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ff467bf5fcf13592c796836def36e16e34f8cc31 99fcf0399006de16d0ac7cc9057564d307cb981b -->


```
INSERT INTO Person VALUES (1,'John');
INSERT INTO Person VALUES (2,'Mary');
INSERT INTO Person VALUES (3,'Alice');
INSERT INTO Person VALUES (4,'Jacob');
INSERT INTO Person VALUES (5,'Julie');

INSERT INTO Restaurant VALUES (1,'Taco Dell','Bellevue');
INSERT INTO Restaurant VALUES (2,'Ginger and Spice','Seattle');
INSERT INTO Restaurant VALUES (3,'Noodle Land', 'Redmond');

INSERT INTO City VALUES (1,'Bellevue','wa');
INSERT INTO City VALUES (2,'Seattle','wa');
INSERT INTO City VALUES (3,'Redmond','wa');

-- Insert into edge table. While inserting into an edge table, 
-- you need to provide the $node_id from $from_id and $to_id columns.
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 1), 
       (SELECT $node_id FROM Restaurant WHERE id = 1),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 2), 
      (SELECT $node_id FROM Restaurant WHERE id = 2),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 3), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 4), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 5), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);

INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 1),
      (SELECT $node_id FROM City WHERE id = 1));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 2),
      (SELECT $node_id FROM City WHERE id = 2));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 3),
      (SELECT $node_id FROM City WHERE id = 3));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 4),
      (SELECT $node_id FROM City WHERE id = 3));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 5),
      (SELECT $node_id FROM City WHERE id = 1));

INSERT INTO locatedIn VALUES ((SELECT $node_id FROM Restaurant WHERE id = 1),
      (SELECT $node_id FROM City WHERE id =1));
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sysfngetauditfile-transact-sqlsystem-functionssys-fn-get-audit-file-transact-sqlmd"></a>2. &nbsp; [sys.fn_get_audit_file (TRANSACT-SQL)](system-functions/sys-fn-get-audit-file-transact-sql.md)

*Updated: 2017-05-16* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_1) | [Next](#TitleNum_3))

<!-- Source markdown line 145.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 046fa92ad1b7e6bb7a956493ca06cf72d45b5285 fbf55361da90663835d7e107fda697c358e0e061 -->



- **Azure SQL データベース**

  この例では、`ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel` という名前のファイルから読み取ります。  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel',default,default);
  GO  
  ```  

  この例では、すべての監査ログで始まるサーバーからは読み取り`Sh`です。  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/Sh',default,default);
  GO  
  ```





&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-manage-retention-of-historical-data-in-system-versioned-temporal-tablestablesmanage-retention-of-historical-data-in-system-versioned-temporal-tablesmd"></a>3.&nbsp;[システム バージョン管理されたテンポラル テーブルの履歴データの保有期間管理](tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)

*Updated: 2017-05-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_2))

<!-- Source markdown line 425.  ms.author= "carlrab".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ee69beb6a46913934d4a322f5d95343cc86f2ec4 94da98fec4ab16636a4581c16eb4456e2d1ff66b -->



**テンポラル履歴保有期間ポリシーのアプローチを使用します。**

> **注:**テンポラル履歴保有期間ポリシーを使用する方法は [!INCLUDE [sqldbesa--../../includes/sqldbesa-md.md)]、SQL Server 2017 年 1 CTP 1.3 から開始します。  

テンポラル履歴の保有期間を指定できます、個々 のテーブル レベルで構成されている、ポリシーを柔軟なエージングを作成できます。 テンポラルの保有期間を適用することは簡単: 1 つだけのパラメーター テーブルの作成時またはスキーマの変更時に設定する必要があります。

保有ポリシーを定義した後、Azure SQL データベースは対象データの自動クリーンアップの履歴行があるかどうかを定期的に確認を開始します。 一致する行の id および履歴テーブルからそれらの削除のスケジュール設定し、システムによって実行されるバック グラウンド タスクの透過的に行われます。 Age 状態、履歴テーブルの行は、SYSTEM_TIME 期間の終了を表す列に基づいてがチェックされます。 たとえば、保有期間は 6 か月間に設定は、クリーンアップの対象となるテーブルの行は、次の条件を満たしています。
```
ValidTo < DATEADD (MONTH, -6, SYSUTCDATETIME())
```
前の例では、ValidTo 列は、SYSTEM_TIME 期間の終了に対応していることと見なされます。
**保有ポリシーを構成する方法は?**

テンポラル テーブルの保有ポリシーを構成する前にまず、データベース レベルでテンポラル履歴保有期間が有効になっているかどうか。
```
SELECT is_temporal_history_retention_enabled, name
FROM sys.databases
```
データベースのフラグ**is_temporal_history_retention_enabled**既定では、ON に設定されているが、ユーザーが ALTER DATABASE ステートメントを使用して変更できます。 ポイントイン タイム復元操作後に OFF に自動的に設定されます。 データベースの一時的な履歴保有期間のクリーンアップを有効にするには、次のステートメントを実行します。
```
ALTER DATABASE <myDB>
SET TEMPORAL_HISTORY_RETENTION  ON
```
保持ポリシーは、ヒストリは削除パラメーターの値を指定することによってテーブルの作成中に構成されます。
```
CREATE TABLE dbo.WebsiteUserInfo
```





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>最近更新されたアーティクルの圧縮のリスト

この圧縮リストは、前のセクションに記載されているすべての更新されたアーティクルへのリンクを提供します。

1. [グラフのデータベースを作成し、T-SQL を使用してクエリに一致するパターンを実行](#TitleNum_1)
2. [sys.fn_get_audit_file (TRANSACT-SQL)](#TitleNum_2)
3. [システム バージョン管理されたテンポラル テーブルの履歴データの保有期間管理](#TitleNum_3)


<a name="sisters2"/>

&nbsp;

## <a name="sister-articles"></a>関連記事

このセクションには、同じの GitHub リポジトリ内の他のサブジェクト領域の最近更新されたアーティクルのアーティクルを非常に似ていますが一覧表示します。


&nbsp;

[Microsoft/**sql docs-pr** ](https://github.com/microsoftdocs/sql-docs-pr/) GitHub.com 上のリポジトリ。

- [最近更新された:**リレーショナル データベースおよび Microsoft SQL Server** docs](/sql/relational-databases/relational-databases-new-updated-sql-docs-pr)
- [最近更新された: **Microsoft SQL Server** docs](/sql/sql-server/sql-server-new-updated-sql-docs-pr)
- [最近更新された: **SQL server TRANSACT-SQL** docs](/sql/t-sql/t-sql-new-updated-sql-docs-pr)


&nbsp;

<!--
[Microsoft/**azure-docs**](https://github.com/microsoft/azure-docs/) repository on GitHub.com:

- [Sisters list for **azure-docs** repo](https://docs.microsoft.com/azure/sql-server-new-updated-azure-docs/#sisters2)
-->

&nbsp;



