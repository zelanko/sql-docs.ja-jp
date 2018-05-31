---
title: Azure SQL DW アップロード タスク | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.component: control-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPDWUPTASK.F1
- sql14.dts.designer.afpdwuptask.f1
ms.assetid: eef82c89-228a-4dc7-9bd0-ea00f57692f5
caps.latest.revision: 5
author: Lingxi-Li
ms.author: lingxl
manager: craigg
ms.openlocfilehash: 8da49de795c0a0fbc8d6da2cf28374a07d7f8778
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
ms.locfileid: "34322463"
---
# <a name="azure-sql-dw-upload-task"></a>Azure SQL DW アップロード タスク
**Azure SQL DW アップロード タスク** を利用すると、SSIS パッケージで、Azure SQL Data Warehouse (DW) のテーブルにローカル データをアップロードできます。 現在サポートされているソース データ ファイル形式は、UTF8 エンコーディングの区切り記号付きテキストです。 アップロード プロセスは、効率的な PolyBase 手法で行われます。この手法に関する説明は、「[Azure SQL Data Warehouse Loading Patterns and Strategies](https://blogs.msdn.microsoft.com/sqlcat/2017/05/17/azure-sql-data-warehouse-loading-patterns-and-strategies/)」 (Azure SQL Data Warehouse の読み込みパターンと戦略) という記事にあります。 具体的には、データは最初に Azure Blob Storage にアップロードされ、それから Azure SQL DW にアップロードされます。 そのため、このタスクを利用するには Azure Blob Storage アカウントが必要になります。

**Azure SQL DW アップロード タスク**は、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。

**Azure SQL DW アップロード タスク**を追加するには、SSIS ツールボックスからデザイナー キャンバスにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして **[編集]** をクリックし、タスク エディター ダイアログ ボックスを表示します。

**[全般]** ページで、次のプロパティを構成します。

フィールド|[説明]
-----|-----------
LocalDirectory|アップロードするデータ ファイルを含むローカル ディレクトリを指定します。
Recursively|サブディレクトリを再帰的に検索するかどうかを指定します。
FileName|特定の名前のパターンを持つファイルを選択する名前フィルターを指定します。 例: MySheet*.xsl\* の場合、MySheet001.xsl や MySheetABC.xslx などのファイルが含まれます。
[RowDelimiter]|各行の終わりに印を付ける文字を指定します。
[列区切り記号]|各列の終わりに印を付ける 1 つ以上の文字を指定します。 例: &#124; (パイプ)、\t (タブ)、' (単一引用符)、" (二重引用符)、および 0x5c (バック スラッシュ)。
IsFirstRowHeader|各データ ファイルの最初の行に実際のデータの代わりに列名を含めるかどうかを指定します。
AzureStorageConnection|Azure Storage 接続マネージャーを指定します。
BlobContainer|ローカル データをアップロードし、PolyBase 経由で Azure DW にリレーする BLOB コンテナーの名前を指定します。 コンテナーが存在しない場合、新規作成されます。
BlobDirectory|ローカル データをアップロードし、PolyBase 経由で Azure DW にリレーする BLOB ディレクトリ (仮想階層構造) を指定します。
RetainFiles|Azure Storage にアップロードしたファイルを保持するかどうかを指定します。
CompressionType|Azure Storage にファイルをアップロードするときに使用する圧縮形式を指定します。 ローカル ソースは影響を受けません。
CompressionLevel|圧縮形式に使用する圧縮レベルを指定します。
AzureDwConnection|Azure SQL DW の ADO.NET 接続マネージャーを指定します。
TableName|アップロード先のテーブルの名前を指定します。 既存のテーブル名を選択するか、**[\<新しいテーブル...>]** を選択して新規作成します。
TableDistribution|新しいテーブルの配布方法を指定します。 **TableName**に新しいテーブル名が指定されている場合に適用されます。
HashColumnName|ハッシュ テーブル配分に使用される列を指定します。 **TableDistribution** に **HASH**が指定されている場合に適用されます。

新しいテーブルと既存のテーブルにいずれにアップロードするかに基づき、異なる **[マッピング]** ページが表示されます。 前者の場合、マッピングするアップロード元の列とそれに対応する、作成予定のアップロード先のテーブルの名前を構成します。 後者の場合、アップロード元の列とアップロード先の列の間のマッピング関係を構成します。

**[列]** ページで、マッピング元ごとのデータ型プロパティを構成します。

**[T-SQL]** ページには、Azure Blob Storage から Azure SQL DW にデータを読み込むための T-SQL が表示されます。 T-SQL は別のページの構成から自動生成され、タスク実行の一部として実行されます。 生成された T-SQL を特定のニーズに合わせて手動で編集することもできます。 **[編集]** ボタンをクリックしてください。 **[リセット]** ボタンをクリックすれば、自動的に生成されたものに後で戻すことができます。

