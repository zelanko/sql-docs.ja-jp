---
title: "ファイルまたはレポートをアップロードする (レポート マネージャー) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "レポートのパブリッシュ [Reporting Services], ファイルのアップロード"
  - "レポート [Reporting Services], パブリッシュ"
  - "レポートのアップロード [Reporting Services]"
  - "ファイルのアップロード [Reporting Services]"
  - "ファイル [Reporting Services], アップロード"
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
caps.latest.revision: 42
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 42
---
# ファイルまたはレポートをアップロードする (レポート マネージャー)
  レポート マネージャーには、レポート、モデル、およびその他のファイルをクライアント アプリケーションからパブリッシュしなくてもレポート サーバーに追加できるアップロード機能が備わっています。 ファイル システムからアップロードしたファイルは、レポート サーバー上のアイテムとして格納されます。 ファイルがどのように格納されるかは、アップロードするファイルの種類によって異なります。  
  
-   .rdl ファイルはレポートとして保存されます。  
  
-   .smdl ファイルはレポート モデルとして格納されます。  
  
-   共有データ ソース (.rds) ファイルなど、その他すべてのファイルはリソースとしてアップロードされます。 リソースはレポート サーバーでは処理されませんが、レポート サーバーが MIME タイプのファイルをサポートしていれば、レポート マネージャーで表示できます。  
  
### ファイルまたはレポートをアップロードするには  
  
1.  [レポート マネージャー (SSRS ネイティブ モード)](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md) を開始します。  
  
2.  レポート マネージャーで **[コンテンツ]** ページに移動します。 アイテムを追加するフォルダーに移動します。  
  
3.  **[ファイルのアップロード]** をクリックします。  
  
4.  **[参照]** をクリックして、アップロードするファイルを選択します。 レポート定義ファイル、画像、ドキュメント、またはレポート サーバーで利用できるようにする任意のファイルをアップロードできます。  
  
5.  新しいアイテムの名前を入力します。 アイテム名ではスペースを使用できます。ただし、予約文字 (; ? : @ & = + , $ / * \< > |) は使用できません : @ & = + , $ / * \< > |.  
  
6.  既存のアイテムを新しいアイテムに置き換える場合は、**[アイテムが存在する場合は上書きする]** をクリックします。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## 参照  
 [共有データ ソースを作成、削除、または変更する (レポート マネージャー)](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)   
 [[コンテンツ] ページ (レポート マネージャー)](../Topic/Contents%20Page%20\(Report%20Manager\).md)   
 [[ファイルのアップロード] ページ (レポート マネージャー)](../Topic/Upload%20File%20Page%20\(Report%20Manager\).md)   
 [フォルダーへのファイルのアップロード](../../reporting-services/report-server/upload-files-to-a-folder.md)  
  
  