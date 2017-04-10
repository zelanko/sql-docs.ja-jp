---
title: "属性値を要求する (マスター データ サービス) | Microsoft Docs"
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
  - "ビジネス ルール [マスター データ サービス], 属性値の要求"
  - "属性 [マスター データ サービス], 値の要求"
ms.assetid: a360ef13-0c34-43b8-a87e-2f5d8732d30e
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# 属性値を要求する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で、マスター データが完全であることを保証するために属性値を要求します。  
  
> [!NOTE]  
>  ドメイン ベースの属性値がないメンバーは、それらのリレーションシップに基づく派生階層に表示されません。  
  
## 前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、次を参照してください。 [管理者と #40 です。マスター データ サービスと #41;](../master-data-services/administrators-master-data-services.md)です。  
  
### 属性値を要求するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  メニュー バーから **[管理]** をポイントして **[ビジネス ルール]**をクリックします。  
  
3.   **ビジネス ルール** ] ページから、 **モデル** ドロップダウン リストでモデルを選択します。  
  
4.   **エンティティ** ボックスで、エンティティを選択します。  
  
5.   **メンバー型** ボックスの一覧に適用するビジネス ルールのメンバーの種類を選択します。  
  
6.  **[追加]**をクリックします。  
  
7.  **[名前]** ボックスにビジネス ルールの名前を入力します。  
  
8.  必要に応じて、 **[説明]** フィールドに、ビジネス ルールの説明を入力します。  
  
9. 下にある、 **、** をブロックする] をクリックして **追加**します。 パネルが表示されます。  
  
10.  **演算子** ドロップダウン リストで、 **アクションに必要な**です。  
  
11.  **属性** ボックスで、属性を選択します。  
  
12. **[保存]**をクリックします。 新しい行が **Then** グリッドに追加されます。  
  
13. **[保存]**をクリックします。  
  
14. **[すべてパブリッシュ]**をクリックします。  
  
15. 確認のダイアログ ボックスで **[OK]**をクリックします。 **[ビジネス ルールの状態]** 列の値は **[アクティブ]**です。  
  
## 次の手順  
  
-   以下のいずれかの手順でビジネス ルールをデータに適用します。  
  
    -   [ビジネス ルールと #40; に対して特定のメンバーを検証します。マスター データ サービスと #41 です。](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [#40; (&)、ビジネス ルールに対してバージョンを検証します。マスター データ サービスと #41 です。](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## 参照  
 [ビジネス ルールと #40 です。マスター データ サービスと #41 です。](../master-data-services/business-rules-master-data-services.md)   
 [派生階層と #40 です。マスター データ サービスと #41 です。](../master-data-services/derived-hierarchies-master-data-services.md)  
  
  