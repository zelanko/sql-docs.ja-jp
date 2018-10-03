---
title: データセットのプロパティ] ダイアログ ボックスの [クエリ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10160"
- sql12.rtp.rptdesigner.datasetproperties.query.f1
ms.assetid: 1fa34a4b-7de0-4e92-99fa-bc28a206773f
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7a9a15146c6abbcad899f9af3c9fb5e665b76fa9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205953"
---
# <a name="dataset-properties-dialog-box-query"></a>[クエリ] ([データセットのプロパティ] ダイアログ ボックス)
  選択**クエリ**で、**データセットのプロパティ** ダイアログ ボックスに、データ ソースを選択し、クエリを作成します。  
  
 **[データセットのプロパティ]** ダイアログ ボックスには、次のカテゴリがあります。  
  
-   [[パラメーター] ([データセットのプロパティ] ダイアログ ボックス)](report-data/dataset-properties-dialog-box-parameters.md)  
  
-   [[フィールド] ([データセットのプロパティ] ダイアログ ボックス)](../../2014/reporting-services/dataset-properties-dialog-box-fields.md)  
  
-   [[オプション] ([データセットのプロパティ] ダイアログ ボックス)](../../2014/reporting-services/dataset-properties-dialog-box-options.md)  
  
-   [[フィルター] ([データセットのプロパティ] ダイアログ ボックス)](report-data/dataset-properties-dialog-box-filters.md)  
  
## <a name="options"></a>および  
 **名前**  
 データセットの名前を入力します。 名前は、レポートのすべてのデータ領域名またはグループ名と異なっている必要があります。  
  
 **Data Source**  
 データセットが基づくデータ ソースを選択します。 新しいデータ ソースを作成するには、 **[新規作成]** をクリックします。  
  
 **[クエリの種類]**  
 データセットに使用するコマンドまたはクエリの種類を選択します。 データベースからデータを取得するクエリを実行するには、 **[テキスト]** を選択します。 **の** TableDirect **機能を使用してテーブル内のすべてのフィールドを選択するには、** [テーブル] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を選択します。 名前を指定してストアド プロシージャを実行するには、 **[ストアド プロシージャ]** を選択します。 既定では、ほとんどのクエリに使用される **[テキスト]** が選択されています。 選択したデータ ソース クエリを編集するには、 **[クエリ デザイナー]** をクリックします。  
  
> [!NOTE]  
>  すべての種類のクエリがすべてのデータ ソースでサポートされるとは限りません。 たとえば、 **テーブル** をサポートしているデータ ソースの種類は **OLE DB** および **ODBC**のみです。  
  
 **[データセットのプロパティ]**  
 このオプションは、コマンドの種類のオプションとして **[テキスト]** を選択したときに表示されます。 クエリを入力するか、 **[インポート]** をクリックして既存のクエリをインポートします。 式を編集するには、 **「式」** (*fx*) ボタンをクリックします。  
  
> [!NOTE]  
>  クエリ デザイナーを使用してクエリを作成した場合は、クエリのテキストがこのボックスに表示されます。  
  
 **テーブル名**  
 データセットとして使用するテーブルの名前を入力します。 このオプションは **[テーブル]** を選択したときに表示されます。  
  
 **[ストアド プロシージャ名の選択または入力]**  
 使用するストアド プロシージャの名前を入力または選択します。 式を編集するには、 **[式]** (*fx*) ボタンをクリックします。 このオプションは、コマンドの種類のオプションとして [ストアド プロシージャ] を選択したときに表示されます。  
  
 **[タイムアウト (秒)]**  
 クエリがタイムアウトするまでの期間を秒数で入力します。既定値は 30 秒です。 **[タイムアウト]** には、値を指定しないか、0 より大きい値を指定する必要があります。 空の場合は、クエリはタイムアウトしません。  
  
## <a name="see-also"></a>参照  
 [データ接続、データ ソース、および Reporting Services の接続文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [レポートにデータを追加&#40;レポート ビルダーおよび SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [クエリ デザイナー &#40;レポート ビルダー&#41;](../../2014/reporting-services/query-designers-report-builder.md)   
 [Reporting Services クエリ デザイナー](../../2014/reporting-services/reporting-services-query-designers.md)  
  
  
