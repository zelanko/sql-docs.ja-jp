---
title: リソース ガバナーを無効にしたとき | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, disabling
ms.assetid: 2c2d2db0-34a5-4f50-b783-17693e3ce3f1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e03786f02e93b40b0b8c4e0132addbbe68395590
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627440"
---
# <a name="disable-resource-governor"></a>リソース ガバナーを無効にしたとき
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  リソース ガバナーを無効にするには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または Transact-SQL を使用します。  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **リソース ガバナーの無効化に使用するもの:**  [オブジェクト エクスプローラー](#RGOffObjEx)、 [リソース ガバナーのプロパティ](#RGOffProp)、 [Transact-SQL](#RGOffTSQL)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
 リソース ガバナーを無効にすると、結果は次のようになります。  
  
-   分類子関数は実行されません。  
  
-   すべての新しい接続が、既定のワークロード グループに自動的に分類されます。  
  
-   システムによって開始される要求は、内部ワークロード グループに分類されます。  
  
-   ワークロード グループとリソース プールの既存の設定は、すべて既定値にリセットされます。 この場合、制限に達してもイベントは発生しません。  
  
-   通常のシステム監視は影響を受けません。  
  
-   構成は変更できますが、リソース ガバナーを有効にするまで変更は反映されません。  
  
-   SQL Server の再起動時に、リソース ガバナーはその構成を読み込みません。このとき、既定および内部のワークロード グループとリソース プールのみが存在します。  
  
###  <a name="LimitationsRestrictions"></a> 制限事項と制約事項  
 ユーザー トランザクション内でリソース ガバナーを無効にする場合、 **ALTER RESOURCE GOVERNOR** ステートメントを使用できません。  
  
###  <a name="Permissions"></a> Permissions  
 リソース ガバナーを無効にするには、CONTROL SERVER 権限が必要です。  
  
##  <a name="RGOffObjEx"></a> オブジェクト エクスプローラーを使用してリソース ガバナーを無効にする  
 **オブジェクト エクスプローラーを使用してリソース ガバナーを無効にするには**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを開き、 **[管理]** ノードを **[リソース ガバナー]** ノードまで再帰的に展開します。  
  
2.  **[リソース ガバナー]** を右クリックし、 **[無効化]** をクリックします。  
  
##  <a name="RGOffProp"></a> リソース ガバナーのプロパティを使用してリソース ガバナーを無効にする  
 **[リソース ガバナーのプロパティ] ページでリソース ガバナーを無効にするには**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプローラーを開き、 **[管理]** ノードを **[リソース ガバナー]** ノードまで再帰的に展開します。  
  
2.  **[リソース ガバナー]** を右クリックし、 **[プロパティ]** をクリックすると、 **[リソース ガバナーのプロパティ]** ページが開きます。  
  
3.  **[リソース ガバナーの有効化]** チェック ボックスをオフにして、 **[OK]** をクリックします。  
  
##  <a name="RGOffTSQL"></a> Transact-SQL を使用してリソース ガバナーを無効にする  
 **Transact-SQL を使用してリソース ガバナーを無効にするには**  
  
1.  **ALTER RESOURCE GOVERNOR DISABLE** ステートメントを実行します。  
  
### <a name="example-transact-sql"></a>例 (Transact-SQL)  
 リソース ガバナーを有効にする例を次に示します。  
  
```  
ALTER RESOURCE GOVERNOR DISABLE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [[リソース ガバナー]](../../relational-databases/resource-governor/resource-governor.md)   
 [リソース ガバナーの有効化](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [リソース ガバナー ワークロード グループ](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [リソース ガバナーの分類子関数](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
