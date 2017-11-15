---
title: "更新 - リレーショナル データベース ドキュメント | Microsoft Docs"
description: "最近変更されたリレーショナル データベースに関するドキュメントで更新されたコンテンツのスニペットを示します。"
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
ms.date: 09/27/2017
ms.author: genemi
ms.openlocfilehash: 70cb071dc7b6f4ff15c5c7dee3f24bb352d6eb61
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>新規または最近の更新: リレーショナル データベース ドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新日の範囲:* &nbsp; **2017 年 9 月 11 日**&nbsp;から &nbsp; **2017 年 9 月 27 日**
- *対象領域:* &nbsp; **リレーショナル データベース**。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [SQL Server および Azure SQL Database のデータをインポートおよびエクスポートする](import-export/overview-import-export.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [空間データ型の概要](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-spatial-data-types-overviewspatialspatial-data-types-overviewmd"></a>1.&nbsp; [空間データ型の概要](spatial/spatial-data-types-overview.md)

*更新日: 2017 年 9 月 26 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 27.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 96dd44cf49e96d1d543a629d49de297dba9c1753 2e9629f852ea42a213c7c24831bcfa53e40358f2  (PR=0  ,  Filename=spatial-data-types-overview.md  ,  Dirpath=docs\relational-databases\spatial\  ,  MergeCommitSha40=b33976cf92f23fbb13cee0c353fd40608d002d94) -->



 -  空間データには 2 つの型があります。 **geometry** データ型は平面 (ユークリッド (平面地球)) データをサポートしています。 **geometry** データ型 (平面) は、Open Geospatial Consortium (OGC) Simple Features for SQL Specification version 1.1.0 および SQL MM (ISO 標準) の両方に準拠しています。
 -
 - ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] ではその他に、**geography** データ型もサポートされています。このデータ型は、GPS の緯度経度座標などの楕円体 (球体地球) データを格納します。
 -
 -> [!IMPORTANT]
 -> 空間データ型の機能強化を含め、..!NCLUDE-NotShown--ssSQL11--../../includes/sssql11-md.md)] に導入された空間機能の詳細な説明とサンプルについては、ホワイト ペーパー「[New Spatial Features in SQL Server Code-Named "Denali"](http://go.microsoft.com/fwlink/?LinkId=226407)」 (SQL Server コードネーム "Denali" の新しい空間機能) をダウンロードしてください。
 -
 -##  <a name="objects"></a> 空間データ オブジェクト
 - **geometry** データ型と **geography** データ型は、16 の空間データ オブジェクト (インスタンス型) をサポートしています。 ただし、 *インスタンス化可能*なインスタンス型、つまりデータベース内でインスタンスを作成して使用することができる (インスタンス化できる) インスタンス型は、そのうちの 11 種類のみです。 これらのインスタンスは、親データ型から派生するプロパティによって、 **Points**、 **LineStrings, CircularStrings**、 **CompoundCurves**、 **Polygons**、 **CurvePolygons** 、または **GeometryCollection** 内の複数の **geometry** インスタンスや **geography**インスタンスとして識別されます。 **Geography** 型には、 **FullGlobe**という追加のインスタンス型があります。
 -
 - 次の図は、 **geometry** の階層を表しています。 **geometry** データ型と **geography** データ型はこの階層に基づいています。 **geometry** と **geography** のインスタンス化可能な型は青で示されています。
 -
 - ![geom_hierarchy--../../relational-databases/spatial/media/geom-hierarchy.gif)
 -
 - 図に示されているように、 **geometry** データ型と **geography** データ型のインスタンス化可能な型は **Point**、 **MultiPoint**、 **LineString**、 **CircularString**、 **MultiLineString**、 **CompoundCurve**、 **Polygon**、 **CurvePolygon**、 **MultiPolygon**、および **GeometryCollection**の 10 種類です。 geography データ型には、もう 1 つ **FullGlobe**というインスタンス化可能な型があります。 **geometry** 型および **geography** 型は、特定のインスタンスが適切な形式のインスタンスである限り、明示的に定義されていない場合でも、そのインスタンスを認識できます。 たとえば、STPointFromText() メソッドを使用して **Point** インスタンスを明示的に定義した場合、そのインスタンスは、メソッドの入力が適切な形式である限り、 **geometry** と **geography** によって **Point**として認識されます。 `STGeomFromText()` メソッドを使用して同じインスタンスを定義した場合は、 **geometry** データ型と **geography** データ型の両方で **Point**として認識されます。







## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新規 + 更新 (0 + 1): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (0 + 1): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (4 + 1): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (17 + 0): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (3 + 0): **Linux 上の SQL** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (1 + 1): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (2 + 0): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (0 + 1): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 0): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (0 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **Tools for SQL**  に関するドキュメント](../tools/new-updated-tools.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


