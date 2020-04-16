---
title: テキストベースのクエリ デザイナのユーザー インターフェイス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10010"
- sql12.rtp.rptdesigner.dataview.genericquerydesigner.f1
helpviewer_keywords:
- text-based query designer [Reporting Services]
- query designers [Reporting Services], text-based
ms.assetid: 44b7c664-03aa-494e-a484-052b318e810c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 340040a0806a87d55582356d085ab924e25b6a48
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388676"
---
# <a name="text-based-query-designer-user-interface"></a>テキストベースのクエリ デザイナーのユーザー インターフェイス
  デザイン時に、データ ソースでサポートされているクエリ言語でクエリを指定し、クエリを実行し、結果を表示するには、テキスト ベースのクエリ デザイナーを使用します。 複数の [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメント、カスタム データ処理拡張機能のクエリまたはコマンド構文、および式としてのクエリを指定できます。 テキスト ベースのクエリ デザイナーはクエリを前処理せず、あらゆる種類のクエリ構文に対応できるため、これは多くの種類のデータ ソースで既定のクエリ デザイナー ツールになっています。

 テキスト ベースのクエリ デザイナーでは、ツール バーと次の 2 つのペインが表示されます。

-   **クエリ**クエリ テキスト、テーブル名、またはストアド プロシージャ名が表示されます。

-   **[結果]** デザイン時にクエリの実行結果が表示されます。

## <a name="text-based-query-designer-toolbar"></a>テキスト ベースのクエリ デザイナーのツール バー
 テキスト ベースのクエリ デザイナーで使用できるツール バーは、コマンドの種類に関係なく 1 つだけです。 次の表は、ツール バーの各ボタンとその機能を示しています。

|Button|説明|
|------------|-----------------|
|**[テキストとして編集]**|テキスト ベースのクエリ デザイナーと、グラフィカル クエリ デザイナー間で切り替えます。 すべての種類のデータ ソースでグラフィカル クエリ デザイナーがサポートされているとは限りません。|
|[**インポート**]|ファイルまたはレポートから既存のクエリをインポートします。 サポートされているファイルの種類は sql と rdl だけです。 詳細については、「 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)と呼ばれます。|
|![クエリの実行](../analysis-services/media/rsqdicon-run.gif "クエリの実行")|クエリを実行し、その結果セットを結果ペインに表示します。|
|**[コマンドの種類]**|**[Text]**、 **[StoredProcedure]**、または **[TableDirect]** を選択します。 パラメーターを受け取るストアド プロシージャの場合、ツール バーの **[実行]** をクリックすると、 **[クエリ パラメーターの定義]** ダイアログ ボックスが表示され、必要な値を入力できます。 ストアド プロシージャが複数の結果セットを返す場合、データセットの設定には最初の結果セットのみが使用されます。<br /><br /> サポートされるコマンドの種類は、データ ソースの種類によって異なります。 たとえば、 **[TableDirect]** がサポートされるのは、OLE DB と ODBC だけです。|

### <a name="command-type-text"></a>コマンドの種類 (Text)
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データセットを作成するとき、レポート デザイナーには既定によりグラフィカル クエリ デザイナーが表示されます。 テキスト ベースのクエリ デザイナーに切り替えるには、ツール バーの **[テキストとして編集]** 切り替えボタンをクリックします。 テキスト ベースのクエリ デザイナーは、クエリ ペインと結果ペインの 2 つのペインで構成されています。 次の図に各ペインの名称を示します。

 ![リレーショナル データのクエリに使用する汎用クエリ デザイナー](../analysis-services/media/rsqd-dsaw-sql-generic.gif "リレーショナル データのクエリに使用する汎用クエリ デザイナー")

 次の表に各ペインの機能を示します。

|ペイン|関数|
|----------|--------------|
|クエリ|[!INCLUDE[tsql](../includes/tsql-md.md)] クエリ テキストを表示します。 [!INCLUDE[tsql](../includes/tsql-md.md)] クエリを記述または編集する際に、このペインを使用します。|
|結果|クエリの結果を表示します。 クエリを実行するには、任意のペインで右クリックして、 **[実行]** をクリックするか、ツール バーの **[実行]** ボタンをクリックします。|

#### <a name="example"></a>例
 次のクエリは、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースの `Contact` テーブルから姓の一覧を取得します。

```
SELECT LastName FROM Person.Person;
```

 `EXEC` ステートメントを含むコマンドの種類 (Text) のすべての [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントを使用できます。 次のクエリでは、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] のストアド プロシージャである `uspGetEmployeeManagers` を呼び出して、識別番号が 1 である従業員の指揮系統を取得しています。

```
EXEC uspGetEmployeeManagers 1;
```

 ツール バーの **[実行]** をクリックすると、 **クエリ** ペインのコマンドが実行され、その結果が **結果** ペインに表示されます。

### <a name="command-type-storedprocedure"></a>コマンドの種類 (StoredProcedure)
 **[コマンドの種類] で [StoredProcedure]** を選択した場合、テキスト ベースのクエリ デザイナーには、クエリ ペインと結果ペインの 2 つのペインが表示されます。 ストアド プロシージャ名をクエリ ペインに入力し、ツール バーの **[実行]** をクリックします。 [クエリ パラメーターの定義] ダイアログ ボックスが表示されます。 ストアド プロシージャのパラメーター値を入力します。 すべてのストアド プロシージャ パラメーターについて、レポート パラメーターが作成されます。

#### <a name="example"></a>例
 次のクエリでは、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] ストアド プロシージャである `uspGetEmployeeManagers` を呼び出します。 クエリを実行する場合は、従業員 ID 番号パラメーターの値を入力する必要があります。

```
uspGetEmployeeManagers;
```

### <a name="command-type-tabledirect"></a>コマンドの種類 (TableDirect)
 **[コマンドの種類] で [TableDirect]** を選択した場合、テキスト ベースのクエリ デザイナーには、クエリ ペインと結果ペインの 2 つのペインが表示されます。 テーブルを入力し、 **[実行]** ボタンをクリックすると、そのテーブルのすべての列が返されます。

#### <a name="example"></a>例
 次のクエリでは、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースのすべての顧客を結果セットとして取得しています。

 `Sales.Customer`

 テーブル名 Sales.Customer を入力すると、[!INCLUDE[tsql](../includes/tsql-md.md)]ステートメント`SELECT * FROM Sales.Customer;`を作成するのと同じになります。

## <a name="see-also"></a>参照
 [レポート デザイナの SQL Server データ ツールのクエリ デザイン ツール &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md) [レポート 埋め込みデータセットと共有データセット&#40;レポート ビルダーおよび SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) SQL Server[接続タイプ&#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md) OLE DB[接続タイプ&#40;SSRS&#41;](report-data/ole-db-connection-type-ssrs.md) ODBC 接続タイプ&#40;レポート ビルダーおよび&#41;[SSRS &#40;レポート ビルダーおよび SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [RSReportDesigner 構成ファイル](report-server/rsreportdesigner-configuration-file.md)&#40;[ODBC Connection Type &#40;SSRS&#41;](report-data/odbc-connection-type-ssrs.md)


