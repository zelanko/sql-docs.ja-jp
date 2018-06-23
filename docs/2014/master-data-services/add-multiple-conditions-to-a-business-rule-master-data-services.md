---
title: ビジネス ルールに複数の条件を追加する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e5ac7bab7712a268e3fe8fd37f1a5ae799ef55dc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163899"
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a>ビジネス ルールに複数の条件を追加する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ではより複雑なルールが必要な場合に、複数の **AND** 条件または **OR** 条件をビジネス ルールに追加します。  
  
> [!NOTE]  
>  **OR** 演算子を使用するビジネス ルールを作成する場合は、個別に評価できる条件ステートメントごとに個別のルールを作成することを検討してください。 そうすることによって、必要に応じてルールを除外できるので、柔軟性が向上し、トラブルシューティングも容易になります。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](administrators-master-data-services.md)」を参照してください。  
  
-   ビジネス ルールが存在する必要があります。 詳細については、「[ビジネス ルールを作成しパブリッシュする (マスター データ サービス)](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)」を参照してください。  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a>ビジネス ルールに複数の条件を追加するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。  
  
3.  **[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。  
  
4.  **[エンティティ]** の一覧からエンティティを選択します。  
  
5.  **メンバー型**一覧で、メンバーの種類を選択します。  
  
6.  **[属性]** の一覧で、属性を選択するか、 **[すべて]** の既定値のままにします。  
  
7.  編集するビジネス ルールの行をクリックします。  
  
8.  **[選択したビジネス ルールの編集]** をクリックします。  
  
9. **コンポーネント** ウィンドウで、展開、**論理演算子**ノード。  
  
10. をクリックして**AND**または**OR**ドラッグして、 **IF**ペインの**AND**ラベル。  
  
11. **[コンポーネント]** ペインで **[条件]** ノードを展開します。  
  
12. 条件をクリックしてドラッグする**場合**ウィンドウに、 **AND**または**OR**手順 10 からのラベル。  
  
13. **属性** ウィンドウで、属性をクリックしておよびドラッグして、**条件の編集**ペインの**属性の選択**ラベル。  
  
14. **条件の編集** ウィンドウで、すべての必須フィールドに入力します。  
  
15. **[条件の編集]** ペインの **[アイテムの保存]** をクリックします。  
  
16. 必要に応じてから他の条件を追加する、**コンポーネント** ウィンドウで、ドラッグ**AND**または**OR**に**AND**または**OR**で、 **IF**ウィンドウです。 手順 13～15 を実行します。  
  
    > [!TIP]  
    >  条件を削除するとに、条件の名前をクリックして、**条件の編集** ウィンドウで、をクリックして**でアイテムの削除**です。  
  
## <a name="see-also"></a>参照  
 [ビジネス ルール&#40;マスター データ サービス&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [ビジネス ルールの名前を変更する &#40;マスター データ サービス&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)   
 [通知を送信するビジネス ルールを構成する&#40;マスター データ サービス&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  