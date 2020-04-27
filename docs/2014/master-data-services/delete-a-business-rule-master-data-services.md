---
title: ビジネス ルールを削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting business rules [Master Data Services]
- business rules [Master Data Services], deleting
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d294bb2d07d87216fb40fb93267518970fdf4c9d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65479745"
---
# <a name="delete-a-business-rule-master-data-services"></a>ビジネス ルールを削除する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、不要になったビジネス ルールを削除します。  
  
> [!NOTE]  
>  ビジネス ルールに対するデータの検証が行われないようにするには、ビジネス ルールを削除する代わりに除外することができます。 詳細については、「 [ビジネス ルールを除外する (マスター データ サービス)](exclude-a-business-rule-master-data-services.md)」を参照してください。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](../../2014/master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-delete-a-business-rule"></a>ビジネス ルールを削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。  
  
3.  **[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。  
  
4.  **[エンティティ]** の一覧からエンティティを選択します。  
  
5.  **[メンバーの種類]** の一覧から、適用するビジネス ルールのメンバーの種類を選択します。  
  
6.  **[属性]** の一覧で、属性を選択するか、 **[すべて]** の既定値のままにします。  
  
7.  グリッドで、削除するビジネス ルールの行をクリックします。  
  
8.  [**選択したビジネスルールの削除**] をクリックします。  
  
9. 確認のダイアログ ボックスで **[OK]** をクリックします。 [**状態**] 列の値が [**削除の保留中**] になっています。  
  
10. **[ビジネス ルールのパブリッシュ]** をクリックします。  
  
11. 確認のダイアログ ボックスで **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [ビジネスルール &#40;マスターデータサービスを除外する&#41;](exclude-a-business-rule-master-data-services.md)   
 [ビジネスルール &#40;マスターデータサービスを作成して発行&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [ビジネス ルール (マスター データ サービス)](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
