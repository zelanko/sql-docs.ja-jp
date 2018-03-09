---
title: "ファイルまたはレポートをアップロードする (レポート マネージャー) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: reports
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
caps.latest.revision: "42"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: bb6634736cc62f16226cb2cfc979d61f136b2f3f
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="upload-a-file-or-report-report-manager"></a>ファイルまたはレポートをアップロードする (レポート マネージャー)
  レポート マネージャーには、レポート、モデル、およびその他のファイルをクライアント アプリケーションからパブリッシュしなくてもレポート サーバーに追加できるアップロード機能が備わっています。 ファイル システムからアップロードしたファイルは、レポート サーバー上のアイテムとして格納されます。 ファイルがどのように格納されるかは、アップロードするファイルの種類によって異なります。  
  
-   .rdl ファイルはレポートとして保存されます。  
  
-   .smdl ファイルはレポート モデルとして格納されます。  
  
-   共有データ ソース (.rds) ファイルなど、その他すべてのファイルはリソースとしてアップロードされます。 リソースはレポート サーバーでは処理されませんが、レポート サーバーが MIME タイプのファイルをサポートしていれば、レポート マネージャーで表示できます。  
  
### <a name="to-upload-a-file-or-report"></a>ファイルまたはレポートをアップロードするには  
  
1.  [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896) を開始します。  
  
2.  レポート マネージャーで **[コンテンツ]** ページに移動します。 アイテムを追加するフォルダーに移動します。  
  
3.  **[ファイルのアップロード]**をクリックします。  
  
4.  **[参照]** をクリックして、アップロードするファイルを選択します。 レポート定義ファイル、画像、ドキュメント、またはレポート サーバーで利用できるようにする任意のファイルをアップロードできます。  
  
5.  新しいアイテムの名前を入力します。 アイテム名ではスペースを使用できます。ただし、予約文字 (; ? : @ & = + , $ / * < > |) は使用できません : @ & = + , $ / * < > |.  
  
6.  既存のアイテムを新しいアイテムに置き換える場合は、 **[アイテムが存在する場合は上書きする]**をクリックします。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [共有データ ソースを作成、削除、または変更する (レポート マネージャー)](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)   
 [[コンテンツ] ページ (レポート マネージャー)](http://msdn.microsoft.com/library/6b16869b-158a-4934-9c85-bee934b35378)   
 [[ファイルのアップロード] ページ &#40;レポート マネージャー&#41;](http://msdn.microsoft.com/library/7bb3166f-9374-4449-b66a-ffb77298507d)   
 [フォルダーへのファイルのアップロード](../../reporting-services/report-server/upload-files-to-a-folder.md)  
  
  
