---
title: '[クエリ] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-data
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- "10024"
- sql13.rtp.rptdesigner.datasetproperties.query.f1
- "10160"
ms.assetid: 75432318-0b00-4797-917c-0a2e74f9d951
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 79bb516e7b23961a79c17c6123d66b8f4985ba63
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33020829"
---
# <a name="dataset-properties-dialog-box-query-report-builder"></a>「クエリ」 (「データセットのプロパティ」 ダイアログ ボックス) (レポート ビルダー)
  **[データセットのプロパティ]** ダイアログ ボックスの **[クエリ]** を選択すると、レポート サーバーから共有データセットを選択したり、埋め込みデータセットを作成したりできます。 埋め込みデータセットを作成するには、データ ソースを選択し、クエリを構築する必要があります。  
  
 **[データセットのプロパティ]** ダイアログ ボックスには、次のカテゴリがあります。  
  
-   [「パラメーター」 (「データセットのプロパティ」 ダイアログ ボックス) &#40;レポート ビルダー&#41;](http://msdn.microsoft.com/library/3a0672ad-c969-455b-b952-585164ce1dda)  
  
-   [「フィールド」 (「データセットのプロパティ」ダイアログ ボックス) &#40;レポート ビルダー&#41;](http://msdn.microsoft.com/library/75c7e54a-3d20-4c9a-88da-ab36dce2ce42)  
  
-   [「オプション」 (「データセットのプロパティ」 ダイアログ ボックス) &#40;レポート ビルダー&#41;](../../reporting-services/report-data/dataset-properties-dialog-box-options-report-builder.md)  
  
-   [「フィルター」 (「データセットのプロパティ」 ダイアログ ボックス) &#40;レポート ビルダー&#41;](http://msdn.microsoft.com/library/933a6f44-4eb7-4e73-9c40-ac0fd17b23d3)  
  
 詳細については、「 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)と呼ばれます。  
  
## <a name="options"></a>および  
 **名前**  
 データセットの名前を入力します。 名前は、レポートのすべてのデータ領域名またはグループ名と異なっている必要があります。  
  
 **[共有データセットを使用する]**  
 レポート サーバーの事前定義済みデータセットを使用するには、このオプションを選択します。  
  
 **[参照]**  
 レポート サーバーまたは SharePoint サイト上のフォルダーを参照し、共有データセット (.rsd) を選択します。  
  
 **[レポート内の埋め込みデータセットを使用する]**  
 このレポートでのみ使用されるデータセットを作成する場合は、このオプションを選択します。  
  
 **[データ ソース]**  
 データセットが基づくデータ ソースを選択します。 新しいデータ ソースを作成するには、 **[新規作成]** をクリックします。  
  
 **[クエリの種類]**  
 データセットに使用するコマンドまたはクエリの種類を選択します。 データベースからデータを取得するクエリを実行するには、 **[テキスト]** を選択します。 **の** TableDirect **機能を使用してテーブル内のすべてのフィールドを選択するには、** [テーブル] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択します。 名前を指定してストアド プロシージャを実行するには、 **[ストアド プロシージャ]** を選択します。 既定では、ほとんどのクエリに使用される **[テキスト]** が選択されています。 選択したデータ ソース クエリを編集するには、 **[クエリ デザイナー]** をクリックします。  
  
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
  
 **[フィールドの更新]**  
 クエリ コマンドを実行して、 [[データセットのプロパティ] ダイアログ ボックスの [フィールド]](http://msdn.microsoft.com/library/75c7e54a-3d20-4c9a-88da-ab36dce2ce42) ページにあるフィールドの一覧を更新します。  
  
## <a name="see-also"></a>参照  
 [レポート データセット (SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [レポート ビルダーのダイアログ ボックス、ペイン、およびウィザードに関するヘルプ](http://msdn.microsoft.com/en-us/2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [クエリ デザイナー &#40;レポート ビルダー&#41;](http://msdn.microsoft.com/library/553f0d4e-8b1d-4148-9321-8b41a1e8e1b9)  
  
  
