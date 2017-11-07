---
title: "SQL Server ドキュメント用の Analysis Services の更新済み - |Microsoft ドキュメント"
description: "更新されたコンテンツで最近変更したドキュメントについては、Microsoft SQL server Analysis Services 用のスニペットを表示します。"
services: na
documentationcenter: 
author: MightyPen
manager: kfile
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: analysis-services
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/27/2017
ms.author: genemi
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: a21f82dd5a0bd4ef59abc639d9441be25191a21b
ms.contentlocale: ja-jp
ms.lasthandoff: 10/02/2017

---
# <a name="new-and-recently-updated-analysis-services-for-sql-server"></a>新規または最近更新された: SQL Server 用に Analysis Services



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新プログラムの日付範囲:* &nbsp; **2017 年-09-11** &nbsp;対&nbsp; **2017 年-09-27**
- *サブジェクト領域:* &nbsp; **for SQL Server Analysis Services**です。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


***今回は新しい記事はありません。***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [どのような &#39; s SQL Server 2017 Analysis Services の新機能](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-what39s-new-in-sql-server-2017-analysis-serviceswhat-s-new-in-sql-server-analysis-services-2017md"></a>1.&nbsp;[何 &#39; s SQL Server 2017 Analysis Services の新機能](what-s-new-in-sql-server-analysis-services-2017.md)

*最終更新日: 2017 年-09-22* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

<!-- Source markdown line 143.  ms.author= "owend".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c8d75883f07e6e32859728d09139920eb9bf65c5 d206e83413d15a6e6116120e4a98dda9c8ce81d8  (PR=3278  ,  Filename=what-s-new-in-sql-server-analysis-services-2017.md  ,  Dirpath=docs\analysis-services\  ,  MergeCommitSha40=656e62f36446db4ef5b232129130a0253d2aebdf) -->



**オブジェクト レベルのセキュリティ**

このリリースには [オブジェクト レベルのセキュリティ--.. が導入されています/analysis-services/tabular-models/object-level-security.md) テーブルと列にします。 テーブルおよび列のデータへのアクセスを制限、だけでなく機密性の高いテーブルおよび列名を保護することができます。 これで、悪意のあるユーザーがテーブルの存在を検出できなくなります。

JSON ベースのメタデータを表形式モデル スクリプト言語 (TMSL)、または表形式オブジェクト モデル (TOM) を使用して、オブジェクト レベルのセキュリティを設定する必要があります。

たとえば、次のコードを使用して、 **TablePermission** クラスの **MetadataPermission** プロパティを **None**に設定すると、サンプル Adventure Works テーブル モデルの Product テーブルをセキュリティで保護できます。

```
//Find the Users role in Adventure Works and secure the Product table
ModelRole role = db.Model.Roles.Find("Users");
Table productTable = db.Model.Tables.Find("Product");
if (role != null && productTable != null)
{
    TablePermission tablePermission;
    if (role.TablePermissions.Contains(productTable.Name))
    {
        tablePermission = role.TablePermissions[productTable.Name];
    }
    else
    {
        tablePermission = new TablePermission();
        role.TablePermissions.Add(tablePermission);
        tablePermission.Table = productTable;
    }
    tablePermission.MetadataPermission = MetadataPermission.None;
}
db.Update(UpdateOptions.ExpandFull);
```

**動的管理ビュー (Dmv)**

[Dmv--../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md) ローカル サーバーの操作とサーバーの正常性に関する情報を返す SQL Server Profiler でクエリします。
このリリースには、機能強化が含まれています。[動的管理ビュー](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services) (DMV) の 1400 1200 互換性レベルは、表形式モデル。







## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新しい + 更新 (0 + 1): **SQL の Advanced Analytics** docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [新しい + 更新 (0 + 1): **SQL 用に Analysis Services** docs](../analysis-services/new-updated-analysis-services.md)
- [新しい + 更新 (4 + 1): **SQL のデータベース エンジン**docs](../database-engine/new-updated-database-engine.md)
- [新しい + 更新 (17 + 0): **sql Integration Services** docs](../integration-services/new-updated-integration-services.md)
- [新しい + 更新 (3 + 0): **SQL の Linux** docs](../linux/new-updated-linux.md)
- [新しい + 更新 (1 + 1):**リレーショナル データベースを SQL** docs](../relational-databases/new-updated-relational-databases.md)
- [新しい + 更新 (2 + 0): **sql Reporting Services** docs](../reporting-services/new-updated-reporting-services.md)
- [新しい + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** docs](../ssms/new-updated-ssms.md)
- [新しい + 更新 (0 + 1): **TRANSACT-SQL** docs](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新しい + 更新 (0 0 以降): **SQL への接続**docs](../connect/new-updated-connect.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新しい + 更新 (0 0 以降): **Microsoft SQL Server** docs](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 0): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (0 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新しい + 更新 (0 0 以降): **Tools for SQL** docs](../tools/new-updated-tools.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)



