---
title: '[クエリ] ([データセットのプロパティ] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10160"
- sql12.rtp.rptdesigner.datasetproperties.query.f1
ms.assetid: 1fa34a4b-7de0-4e92-99fa-bc28a206773f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: aead5d8e5c85b67333f10bee4e73e2bb1a8633ab
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109371"
---
# <a name="dataset-properties-dialog-box-query"></a>[クエリ] ([データセットのプロパティ] ダイアログ ボックス)
  [データセットの**プロパティ**] ダイアログボックスの [**クエリ**] を選択すると、データソースを選択してクエリを作成できます。  
  
 **[データセットのプロパティ]** ダイアログ ボックスには、次のカテゴリがあります。  
  
-   [[パラメーター] ([データセットのプロパティ] ダイアログ ボックス)](report-data/dataset-properties-dialog-box-parameters.md)  
  
-   [[フィールド] ([データセットのプロパティ] ダイアログ ボックス)](../../2014/reporting-services/dataset-properties-dialog-box-fields.md)  
  
-   [[オプション] ([データセットのプロパティ] ダイアログ ボックス)](../../2014/reporting-services/dataset-properties-dialog-box-options.md)  
  
-   [[フィルター] ([データセットのプロパティ] ダイアログ ボックス)](report-data/dataset-properties-dialog-box-filters.md)  
  
## <a name="options"></a>Options  
 **名前**  
 データセットの名前を入力します。 名前は、レポートのすべてのデータ領域名またはグループ名と異なっている必要があります。  
  
 **データ ソース**  
 データセットが基づくデータ ソースを選択します。 新しいデータ ソースを作成するには、 **[新規作成]** をクリックします。  
  
 **クエリの種類**  
 データセットに使用するコマンドまたはクエリの種類を選択します。 データベースからデータを取得するクエリを実行するには、 **[テキスト]** を選択します。 **の** TableDirect **機能を使用してテーブル内のすべてのフィールドを選択するには、** [テーブル] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を選択します。 名前を指定してストアド プロシージャを実行するには、 **[ストアド プロシージャ]** を選択します。 既定では、ほとんどのクエリに使用される **[テキスト]** が選択されています。 選択したデータ ソース クエリを編集するには、 **[クエリ デザイナー]** をクリックします。  
  
> [!NOTE]  
>  すべての種類のクエリがすべてのデータ ソースでサポートされるとは限りません。 たとえば、 **テーブル** をサポートしているデータ ソースの種類は **OLE DB** および **ODBC**のみです。  
  
 **クエリ**  
 このオプションは、コマンドの種類のオプションとして **[テキスト]** を選択したときに表示されます。 クエリを入力するか、 **[インポート]** をクリックして既存のクエリをインポートします。 式を編集するには、**式**([*fx*]) ボタンをクリックします。  
  
> [!NOTE]  
>  クエリ デザイナーを使用してクエリを作成した場合は、クエリのテキストがこのボックスに表示されます。  
  
 **テーブル名**  
 データセットとして使用するテーブルの名前を入力します。 このオプションは **[テーブル]** を選択したときに表示されます。  
  
 **[ストアド プロシージャ名の選択または入力]**  
 使用するストアド プロシージャの名前を入力または選択します。 式を編集するには、**式**([*fx*]) ボタンをクリックします。 このオプションは、コマンドの種類のオプションとして [ストアド プロシージャ] を選択したときに表示されます。  
  
 **[タイムアウト (秒)]**  
 クエリがタイムアウトするまでの秒数を入力します。既定値は30秒です。 **[タイムアウト]** には、値を指定しないか、0 より大きい値を指定する必要があります。 空の場合は、クエリはタイムアウトしません。  
  
## <a name="see-also"></a>参照  
 [Reporting Services のデータ接続、データソース、および接続文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-data/report-datasets-ssrs.md)   
 [クエリデザイナー &#40;レポートビルダー&#41;](../../2014/reporting-services/query-designers-report-builder.md)   
 [Reporting Services クエリ デザイナー](../../2014/reporting-services/reporting-services-query-designers.md)  
  
  
