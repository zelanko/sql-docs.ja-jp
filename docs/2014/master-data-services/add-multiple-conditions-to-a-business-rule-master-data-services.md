---
title: ビジネス ルールに複数の条件を追加する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 54ab01033fc65f829f2a06bb5cbad8fc9e4d08f7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65480178"
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a>ビジネス ルールに複数の条件を追加する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ではより複雑なルールが必要な場合に、複数の **AND** 条件または **OR** 条件をビジネス ルールに追加します。  
  
> [!NOTE]  
>  **OR** 演算子を使用するビジネス ルールを作成する場合は、個別に評価できる条件ステートメントごとに個別のルールを作成することを検討してください。 そうすることによって、必要に応じてルールを除外できるので、柔軟性が向上し、トラブルシューティングも容易になります。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。  
  
-   ビジネス ルールが存在する必要があります。 詳細については、「[ビジネス ルールを作成しパブリッシュする (マスター データ サービス)](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)」を参照してください。  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a>ビジネス ルールに複数の条件を追加するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。  
  
3.  **[ビジネス ルールのメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。  
  
4.  **[エンティティ]** の一覧からエンティティを選択します。  
  
5.  [**メンバーの種類**] ボックスの一覧から、メンバーの種類を選択します。  
  
6.  **[属性]** の一覧で、属性を選択するか、 **[すべて]** の既定値のままにします。  
  
7.  編集するビジネス ルールの行をクリックします。  
  
8.  **[選択したビジネス ルールの編集]** をクリックします。  
  
9. [**コンポーネント**] ウィンドウで、[**論理演算子**] ノードを展開します。  
  
10. [ **And** ] または [ **or** ] をクリックし、[ **IF** ] ペインの **[and** ] ラベルにドラッグします。  
  
11. **[コンポーネント]** ペインで **[条件]** ノードを展開します。  
  
12. 条件をクリックし、[ **IF** ] ペインにドラッグして、手順10の **[And** ] また**は**[] ラベルにドラッグします。  
  
13. [**属性**] ペインで属性をクリックし、[条件の**編集**] ペインの **[属性の選択]** ラベルにドラッグします。  
  
14. [**条件の編集**] ウィンドウで、必要なフィールドを入力します。  
  
15. **[条件の編集]** ペインの **[アイテムの保存]** をクリックします。  
  
16. 必要に応じて、さらに条件を追加するには、[**コンポーネント**]**ペインで** **[And** **] また****は [** **or** ] をドラッグします。 手順 13～15 を実行します。  
  
    > [!TIP]  
    >  条件を削除するには、条件の名前をクリックし、[**条件の編集**] ペインで [項目の**削除**] をクリックします。  
  
## <a name="see-also"></a>参照  
 [ビジネスルール &#40;マスターデータサービス&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [ビジネスルールの名前を変更する &#40;マスターデータサービス&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)   
 [通知を送信するようにビジネス ルールを構成する (マスター データ サービス)](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
