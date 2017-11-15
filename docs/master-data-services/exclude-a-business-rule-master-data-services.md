---
title: "ビジネス ルールを除外する (マスター データ サービス) | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: business rules [Master Data Services], excluding
ms.assetid: bdbc9df0-23f7-40b9-8aba-4445c1482580
caps.latest.revision: "7"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 825c3df3a57b9618ad5ac69f91931c901fe995e0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="exclude-a-business-rule-master-data-services"></a>ビジネス ルールを除外する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、ビジネス ルールを完全に削除せずにそのルールに対するデータの検証が行われないようにする場合は、ビジネス ルールを除外します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-exclude-a-business-rule"></a>ビジネス ルールを除外するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  メニュー バーから **[管理]** をポイントして **[ビジネス ルール]**をクリックします。  
  
3.  **[ビジネス ルール]** ページの **[モデル]** ドロップダウン リストから、モデルを選択します。  
  
4.  **[エンティティ]** ドロップダウン リストから、エンティティを選択します。  
  
5.  **[メンバーの種類]** ドロップ ダウン リストから、メンバーの種類を選択します。  
  
6.  グリッドで、除外するビジネス ルールの行を選択し、 **[編集]**をクリックします。  
  
7.  **[除外]** チェック ボックスをオンにします。  
  
8.  **[保存]**をクリックします。  
  
9. **[すべてパブリッシュ]**をクリックします。  
  
10. 確認のダイアログ ボックスで **[OK]**をクリックします。 **[ビジネス ルールの状態]** 列が **[除外]** になり、 **[除外]** 列が **[はい]**になります。  
  
## <a name="see-also"></a>参照  
 [ビジネス ルールを削除する (マスター データ サービス)](../master-data-services/delete-a-business-rule-master-data-services.md)   
 [ビジネス ルールを作成しパブリッシュする (マスター データ サービス)](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [ビジネス ルール (マスター データ サービス)](../master-data-services/business-rules-master-data-services.md)  
  
  
