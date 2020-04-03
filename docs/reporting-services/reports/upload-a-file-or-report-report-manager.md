---
title: レポート サーバーでファイルまたはレポートをアップロードする | Microsoft Docs
description: レポートやその他のファイルをクライアント アプリケーションからパブリッシュせずにレポート サーバーに追加する方法について説明します。
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6d5d70a2147ea5cb9846ed37ea8963cc8c3f98e3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "79510053"
---
# <a name="upload-a-file-or-report-in-the-report-server"></a>レポート サーバーでファイルまたはレポートをアップロードする
レポート サーバーの Web ポータルには、レポートおよびその他のファイルをクライアント アプリケーションからパブリッシュしなくてもレポート サーバーに追加できるアップロード機能が用意されています。 ファイル システムからアップロードしたファイルは、レポート サーバー上のアイテムとして格納されます。 ファイルがどのように格納されるかは、アップロードするファイルの種類によって異なります。  
  
-   .rdl ファイルはページ分割されたレポートとして保存されます。  
  
-   共有データ ソース (.rds) ファイルなど、その他すべてのファイルはリソースとしてアップロードされます。 リソースはレポート サーバーでは処理されませんが、レポート サーバーが MIME タイプのファイルをサポートしていれば、Web ポータルで表示できます。  
  
### <a name="to-upload-a-file-or-report"></a>ファイルまたはレポートをアップロードするには  
  
1.  Web ポータルで、 **[アップロード]** をクリックします。  
  
4.  アップロードするファイルを参照します。 レポート定義ファイル、画像、ドキュメント、またはレポート サーバーで利用できるようにする任意のファイルをアップロードできます。  
  
5.  新しいアイテムの名前を入力します。 アイテム名ではスペースを使用できますが、次の予約文字は使用できません。\; \? \: \@ \& \= \+ \, \$ \/ \* \< \> \|。  
  
6.  既存のアイテムを新しいアイテムに置き換える場合は、 **[アイテムが存在する場合は上書きする]** をクリックします。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照   
[共有データ ソースを作成、変更、および削除する](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)
[フォルダーへのファイルのアップロード](../../reporting-services/report-server/upload-files-to-a-folder.md)  
  
  
