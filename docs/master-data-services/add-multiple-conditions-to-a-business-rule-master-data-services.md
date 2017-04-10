---
title: "ビジネス ルールに複数の条件を追加する (マスター データ サービス) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ビジネス ルール [マスター データ サービス], 複数の条件"
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# ビジネス ルールに複数の条件を追加する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ではより複雑なルールが必要な場合に、複数の **AND** 条件または **OR** 条件をビジネス ルールに追加します。  
  
> [!NOTE]  
>  **OR** 演算子を使用するビジネス ルールを作成する場合は、個別に評価できる条件ステートメントごとに個別のルールを作成することを検討してください。 そうすることによって、必要に応じてルールを除外できるので、柔軟性が向上し、トラブルシューティングも容易になります。  
  
## 前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
-   ビジネス ルールが存在する必要があります。 詳細については、「[ビジネス ルールを作成しパブリッシュする (マスター データ サービス)](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)」を参照してください。  
  
### ビジネス ルールに複数の条件を追加するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  メニュー バーから **[管理]** をポイントして **[ビジネス ルール]**をクリックします。  
  
3.  **[ビジネス ルール]** ページの **[モデル]** ドロップダウン リストから、モデルを選択します。  
  
4.  **[エンティティ]** ドロップダウン リストから、エンティティを選択します。  
  
5.  **[メンバーの種類]** ドロップ ダウン リストから、メンバーの種類を選択します。  
  
6.  編集するビジネス ルールの行をクリックします。  
  
7.  **[編集]**をクリックします。  
  
8.  **If** ブロックの下で、左側にある論理演算子のドロップダウン リストから、**AND/OR/ NOT** を選択します。  
  
9. **[追加]**をクリックします。 パネルが表示されます。  
  
10. **[属性]** ドロップダウン リストから、属性を選択します。  
  
11. **[演算子]** ドロップダウン リストから、条件を選択します。  
  
12. すべての必須フィールドに入力します。  
  
13. **[保存]**をクリックします。 新しい行が **If** グリッドに追加されます。  
  
14. 他の条件も追加する場合は、手順 8 ～ 13 を繰り返します。  
  
    > [!TIP]  
    >  条件を削除するには、条件を選択して右クリックし、**[削除]** をクリックします。  
  
    > [!TIP]  
    >  複数の条件を選択して右クリックすると、論理演算子内で条件をグループ化したり、特定の論理演算子内の条件のグループ化を解除したりできます。  
  
## 参照  
 [ビジネス ルール (マスター データ サービス)](../master-data-services/business-rules-master-data-services.md)   
 [ビジネス ルールの名前を変更する (マスター データ サービス)](../master-data-services/change-a-business-rule-name-master-data-services.md)   
 [通知を送信するようにビジネス ルールを構成する (マスター データ サービス)](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  