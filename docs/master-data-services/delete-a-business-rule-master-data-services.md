---
title: "ビジネス ルール (マスター データ サービス) の削除 |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting business rules [Master Data Services]
- business rules [Master Data Services], deleting
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6ae93d3c89386382b88b470cbfa3a455302c00c2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="delete-a-business-rule-master-data-services"></a>ビジネス ルールを削除する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で、不要になったビジネス ルールを削除します。  
  
> [!NOTE]  
>  ビジネス ルールに対するデータの検証が行われないようにするには、ビジネス ルールを削除する代わりに除外することができます。 詳細については、「[ビジネス ルールを除外する (マスター データ サービス)](../master-data-services/exclude-a-business-rule-master-data-services.md)」を参照してください。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-delete-a-business-rule"></a>ビジネス ルールを削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  メニュー バーから **[管理]** をポイントして **[ビジネス ルール]**をクリックします。  
  
3.  **[ビジネス ルール]** ページの **[モデル]** ドロップダウン リストから、モデルを選択します。  
  
4.  **[エンティティ]** ドロップダウン リストから、エンティティを選択します。  
  
5.  **[メンバーの種類]** ドロップダウン リストから、適用するビジネス ルールのメンバーの種類を選択します。  
  
6.  グリッドで、削除するビジネス ルールの行をクリックします。  
  
7.  **[削除]**をクリックします。  
  
8.  確認のダイアログ ボックスで **[OK]**をクリックします。 **[ビジネス ルールの状態]** 列の値は **[削除の保留中]**です。  
  
9. **[すべてパブリッシュ]**をクリックします。  
  
10. 確認のダイアログ ボックスで **[OK]**をクリックします。 削除されたビジネス ルールはグリッドに表示されなくなります。  
  
## <a name="see-also"></a>参照  
 [ビジネス ルール &#40; を除外します。マスター データ サービス &#41;](../master-data-services/exclude-a-business-rule-master-data-services.md)   
 [作成して発行するビジネス ルール & #40 です。マスター データ サービス &#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [ビジネス ルール & #40 です。マスター データ サービス &#41;](../master-data-services/business-rules-master-data-services.md)  
  
  
