---
title: "プレビュー データ ダイアログ ボックス (SQL Server インポートおよびエクスポート ウィザード) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.previewdata.f1
ms.assetid: 423ac26a-ba02-4fdf-88b4-07995fe4a97e
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: bfa75d2c1d2d50d1f0205fed22811ddbb3b96747
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="preview-data-dialog-box-sql-server-import-and-export-wizard"></a>[データのプレビュー] ダイアログ ボックス (SQL Server インポートおよびエクスポート ウィザード)
  コピーするデータを指定した後に、必要に応じて **[プレビュー]** をクリックして **[データのプレビュー]** ダイアログ ボックスを開くことができます。 このページでは、データ ソースから最大 200 行のサンプル データをプレビューできます。 プレビューで、コピーしたいデータがウィザードによってコピーされることを確認します。
  
## <a name="screen-shot-of-the-preview-data-page"></a>[データのプレビュー] ページのスクリーン ショット 
 次のスクリーン ショットは、ウィザードの **[データのプレビュー]** ダイアログ ボックスです。  
 
![インポートおよびエクスポート ウィザードのプレビュー データ ページ](../../integration-services/import-export-data/media/preview-data.png "インポートおよびエクスポート ウィザードのプレビュー データ ページ")  
  
## <a name="preview-sample-data"></a>サンプル データのプレビュー  
 **変換元**  
ウィザードがデータ ソースからデータを読み込むために使用しているクエリが表示されます。

コピーするため、テーブルを選択した場合、**ソース**フィールドが表示されます、`SELECT * FROM <table>`テーブル名の代わりにクエリします。 
  
 **サンプル データ グリッド**  
 クエリから返されたデータ ソースのサンプル データが最大 200 行表示されます。  


## <a name="thats-not-right-i-want-to-change-something"></a>何かを変更する権限はないです。
データをプレビューした後で、ウィザードの前のページで選択したオプションを変更してもかまいません。 これらの変更 をクリックして**OK**に戻るには、 **ソース テーブルおよびビュー**  ページで、をクリックして**戻る**を変更前のページに戻るには、選択します。

## <a name="whats-next"></a>次の操作  
 コピーするデータをプレビューしたら、 **[OK]**をクリックします。 **[データのプレビュー]** ダイアログ ボックスから、 **[コピー元のテーブルおよびビューを選択]** ページまたは **[フラット ファイルの変換先の構成]** ページに戻ります。 詳細については、「 [[コピー元のテーブルおよびビューを選択]](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md) 」または「 [[フラット ファイルの変換先の構成]](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md)」を参照してください。  
 
 ## <a name="see-also"></a>参照
[簡単な例によるインポートおよびエクスポート ウィザードの概要](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)

