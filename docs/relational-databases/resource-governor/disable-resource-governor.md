---
title: "Resource Governor を無効にしたとき | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: resource-governor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Resource Governor, disabling
ms.assetid: 2c2d2db0-34a5-4f50-b783-17693e3ce3f1
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 69ff08716168f02736aa5a4ce8eb340fba637bc0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="disable-resource-governor"></a>Resource Governor を無効にしたとき
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Resource Governor を無効にするには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または Transact-SQL を使用します。  
  
-   **作業を開始する準備:**  [制限事項と制約事項](#LimitationsRestrictions)、 [権限](#Permissions)  
  
-   **Resource Governor の無効化に使用するもの:**  [オブジェクト エクスプローラー](#RGOffObjEx)、[Resource Governor　のプロパティ](#RGOffProp)、 [Transact-SQL](#RGOffTSQL)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
 Resource Governor を無効にすると、結果は次のようになります。  
  
-   分類子関数は実行されません。  
  
-   すべての新しい接続が、既定のワークロード グループに自動的に分類されます。  
  
-   システムによって開始される要求は、内部ワークロード グループに分類されます。  
  
-   ワークロード グループとリソース プールの既存の設定は、すべて既定値にリセットされます。 この場合、制限に達してもイベントは発生しません。  
  
-   通常のシステム監視は影響を受けません。  
  
-   構成は変更できますが、Resource Governor を有効にするまで変更は反映されません。  
  
-   SQL Server の再起動時に、Resource Governor はその構成を読み込みません。このとき、既定および内部のワークロード グループとリソース プールのみが存在します。  
  
###  <a name="LimitationsRestrictions"></a> 制限事項と制約事項  
 ユーザー トランザクション内で Resource Governor を無効にする場合、 **ALTER RESOURCE GOVERNOR** ステートメントを使用できません。  
  
###  <a name="Permissions"></a> 権限  
 Resource Governor を無効にするには、CONTROL SERVER 権限が必要です。  
  
##  <a name="RGOffObjEx"></a> オブジェクト エクスプローラーを使用して Resource Governor を無効にする  
 **オブジェクト エクスプローラーを使用して Resource Governor を無効にするには**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを開き、 **[管理]** ノードを **[Resource Governor]**ノードまで再帰的に展開します。  
  
2.  **[Resource Governor]**を右クリックし、 **[無効化]**をクリックします。  
  
##  <a name="RGOffProp"></a> Resource Governor のプロパティを使用して Resource Governor を無効にする  
 **[Resource Governor のプロパティ] ページで Resource Governor を無効にするには**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを開き、 **[管理]** ノードを **[Resource Governor]** ノードまで再帰的に展開します。  
  
2.  **[Resource Governor]** を右クリックし、 **[プロパティ]**をクリックすると、 **[Resource Governor のプロパティ]** ページが開きます。  
  
3.  **[Resource Governor の有効化]** チェック ボックスをオフにして、 **[OK]**をクリックします。  
  
##  <a name="RGOffTSQL"></a> Transact-SQL を使用して Resource Governor を無効にする  
 **Transact-SQL を使用して Resource Governor を無効にするには**  
  
1.  **ALTER RESOURCE GOVERNOR DISABLE** ステートメントを実行します。  
  
### <a name="example-transact-sql"></a>例 (Transact-SQL)  
 Resource Governor を有効にする例を次に示します。  
  
```  
ALTER RESOURCE GOVERNOR DISABLE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [[Resource Governor]](../../relational-databases/resource-governor/resource-governor.md)   
 [Resource Governor の有効化](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Resource Governor リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Resource Governor ワークロード グループ](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Resource Governor の分類子関数](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
