---
title: 属性値を要求する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], requiring attribute values
- attributes [Master Data Services], requiring values
ms.assetid: a360ef13-0c34-43b8-a87e-2f5d8732d30e
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 080f6ef911ee36a8f71efbf3c8783457ac1dc403
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306002"
---
# <a name="require-attribute-values-master-data-services"></a>属性値を要求する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、マスター データが完全であることを保証するために属性値を要求します。  
  
> [!NOTE]  
>  ドメイン ベースの属性値がないメンバーは、それらのリレーションシップに基づく派生階層に表示されません。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-require-attribute-values"></a>属性値を要求するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。  
  
3.  **[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。  
  
4.  **[エンティティ]** の一覧からエンティティを選択します。  
  
5.  **[メンバーの種類]** の一覧から、適用するビジネス ルールのメンバーの種類を選択します。  
  
6.  **[属性]** の一覧で、属性を選択するか、 **[すべて]** の既定値のままにします。  
  
7.  **[ビジネス ルールの追加]** をクリックします。  
  
8.  **[選択したビジネス ルールの編集]** をクリックします。  
  
9. **[コンポーネント]** ペインで **[アクション]** ノードを展開します。  
  
10. をクリックして**が必要な**ドラッグして、**し**ペインの**アクション**ラベル。  
  
11. **[属性]** ペインで属性をクリックして、 **[アクションの編集]** ペインの **[属性の選択]** ラベルにドラッグします。  
  
12. **[アクションの編集]** ペインの **[アイテムの保存]** をクリックします。  
  
13. **[戻る]** をクリックします。  
  
14. 必要に応じて、 **[ビジネス ルールのメンテナンス]** ページで、ビジネス ルールを含む行の **[名前]**、 **[説明]**、または **[通知]** 列のセルをダブルクリックして値を更新します。  
  
15. **[ビジネス ルールのパブリッシュ]** をクリックします。  
  
16. 確認のダイアログ ボックスで **[OK]** をクリックします。 ルールの状態が **[アクティブ]** に変わります。  
  
## <a name="next-steps"></a>次の手順  
  
-   以下のいずれかの手順でビジネス ルールをデータに適用します。  
  
    -   [ビジネス ルールに対して特定のメンバーを検証する&#40;マスター データ サービス&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [ビジネス ルールに対してバージョンを検証&#40;マスター データ サービス&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [ビジネス ルール&#40;マスター データ サービス&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [派生階層&#40;マスター データ サービス&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
