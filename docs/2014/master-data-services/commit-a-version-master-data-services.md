---
title: バージョンをコミットする (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- committing versions [Master Data Services]
- versions [Master Data Services], committing
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 65ac3c0c590a3b5d1fc03ab17625f039c163ac57
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65480030"
---
# <a name="commit-a-version-master-data-services"></a>バージョンをコミットする (マスター データ サービス)
  
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデルのバージョンをコミットして、モデルのメンバーおよびメンバーの属性に対する変更を防止します。 コミットしたバージョンはロック解除できません。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [**バージョン管理**] 機能領域にアクセスするためのアクセス許可が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
-   バージョンのステータスは、 **[ロック済み]** である必要があります。 詳細については、「 [バージョンをロックする (マスター データ サービス)](../../2014/master-data-services/lock-a-version-master-data-services.md)」を参照してください。  
  
-   すべてのメンバーが正常に検証されている必要があります。  
  
### <a name="to-commit-a-version"></a>バージョンをコミットするには  
  
1.  
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]** をクリックします。  
  
2.  
  **[バージョンの管理]** ページのメニュー バーの **[バージョンの検証]** をクリックします。  
  
3.  
  **[バージョンの検証]** ページで、コミットするモデルおよびバージョンを選択します。  
  
4.  
  **[コミット]** をクリックします。  
  
5.  確認のダイアログ ボックスで **[OK]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
  
-   [バージョンフラグ &#40;マスターデータサービスを作成し&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [バージョン &#40;マスターデータサービスにフラグを割り当てる&#41;](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [マスターデータサービス &#40;バージョンをコピー&#41;](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [バージョン &#40;マスターデータサービス&#41;](../../2014/master-data-services/versions-master-data-services.md)  
  
  
