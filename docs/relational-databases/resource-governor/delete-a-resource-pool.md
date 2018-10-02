---
title: リソース プールの削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool delete
- resource pools [SQL Server], delete
ms.assetid: 3bdd348b-6582-4ffa-80ef-d49e50596ce5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ddddbefb8ab2249e96c327392de652e8e877faad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825260"
---
# <a name="delete-a-resource-pool"></a>リソース プールの削除
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  リソース プールを削除にするには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または Transact-SQL を使用します。  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **リソース プールの削除に使用するもの:** [SQL Server Management Studio](#DelRPSSMS)、 [Transact-SQL](#DelRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
 ワークロード グループが含まれている場合は、リソース プールを削除できません。  
  
###  <a name="LimitationsRestrictions"></a> 制限事項と制約事項  
 リソース ガバナーの既定のリソース プールや内部リソース プールを削除することはできません。 ワークロード グループが含まれている場合は、リソース プールを削除できません。 詳細については、「 [Delete a Workload Group](../../relational-databases/resource-governor/delete-a-workload-group.md)」を参照してください。  
  
###  <a name="Permissions"></a> Permissions  
 リソース プールを削除するには、CONTROL SERVER 権限が必要です。  
  
##  <a name="DelRPSSMS"></a> オブジェクト エクスプ ローラーを使用してリソース プールを削除する  
 **SQL Server Management Studio を使用してリソース プールを削除するには**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを開き、 **[管理]** ノードを **[リソース ガバナー]** ノードまで再帰的に展開します。  
  
2.  削除するリソース プールを右クリックし、 **[削除]** をクリックします。  
  
3.  **[オブジェクトの削除]** ウィンドウの **[削除されるオブジェクト]** ボックスの一覧に、リソース プールが表示されます。 リソース プールを削除するには、 **[OK]** をクリックします。  
  
    > [!NOTE]  
    >  ワークロード グループが含まれているリソース プールを削除しようとすると失敗します。  
  
##  <a name="DelRPTSQL"></a> Transact-SQL を使用してリソース プールを削除する  
 **Transact-SQL を使用してリソース プールを削除するには**  
  
1.  削除するリソース プールの名前を指定して **DROP RESOURCE POOL** ステートメントまたは **DROP EXTERNAL RESOURCE POOL** ステートメントを実行します。  
  
2.  **ALTER RESOURCE GOVERNOR RECONFIGURE** ステートメントを実行します。  
  
### <a name="example-transact-sql"></a>例 (Transact-SQL)  
 次の例では、 `poolAdhoc`というワークロード グループを削除します。  
  
```  
DROP RESOURCE POOL poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [[リソース ガバナー]](../../relational-databases/resource-governor/resource-governor.md)   
 [リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [リソース プールの作成](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [リソース プールの設定の変更](../../relational-databases/resource-governor/change-resource-pool-settings.md)   
 [リソース ガバナー ワークロード グループ](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [リソース ガバナーの分類子関数](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [DROP EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)  
  
  
