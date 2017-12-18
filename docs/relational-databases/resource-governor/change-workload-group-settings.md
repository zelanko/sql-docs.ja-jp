---
title: "ワークロード グループの設定の変更 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: resource-governor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- workload groups [SQL Server], alter
- Resource Governor, workload group alter
ms.assetid: 73b6109c-2ad0-4915-b11b-d40d5a0fdc25
caps.latest.revision: "15"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 18c72fb3a7370f557e9e4dc759234d3ea6ad81f3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="change-workload-group-settings"></a>ワークロード グループの設定の変更
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] ワークロード グループの設定を変更するには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用します。  
  
-   **作業を開始する準備:**  [制限事項と制約事項](#LimitationsRestrictions)、 [権限](#Permissions)  
  
-   **ワークロード グループの設定変更に使用するもの:**  [SQL Server Management Studio](#ChgWGProp)、 [Transact-SQL](#ChgWGTSQL)  
  
## <a name="before-you-begin"></a>はじめに  
  
###  <a name="LimitationsRestrictions"></a> 制限事項と制約事項  
 既定のワークロード グループとユーザー定義のワークロード グループの設定を変更することができます。  
  
 **REQUEST_MAX_MEMORY_GRANT_PERCENT**  
  
 非固定パーティション テーブルのインデックス作成によって消費されるメモリは、含まれるパーティションの数に比例します。 必要なメモリの合計が、ワークロード グループの設定によって課せられているクエリごとの制限 (REQUEST_MAX_MEMORY_GRANT_PERCENT) を超えると、インデックス作成の実行に失敗します。 default ワークロード グループでは、SQL Server 2005 との互換性のために、クエリごとの制限を超えてもクエリの開始に必要な最低限のメモリを使用できるようになっているので、そのようなクエリを実行するのに十分な量のメモリが default リソース プールに対して構成されていれば、同じインデックス作成を default ワークロード グループで実行できる可能性があります。  
  
 インデックス作成では、パフォーマンスを向上させるため、最初に許可されたメモリ量を超えるメモリ ワークスペースの使用が許可されます。 この特別な処理はリソース ガバナーでサポートされていますが、最初のメモリ許可も追加のメモリ許可も、ワークロード グループ設定およびリソース プール設定によって制限されます。  
  
###  <a name="Permissions"></a> 権限  
 ワークロード グループの設定を変更するには、CONTROL SERVER 権限が必要です。  
  
##  <a name="ChgWGProp"></a> SQL Server Management Studio を使用してワークロード グループの設定を変更する  
 **ワークロード グループの設定を変更するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  オブジェクト エクスプローラーで、変更するワークロード グループを含む **ワークロード グループ** フォルダーまで **[管理]** ノードを再帰的に展開します。  
  
2.  変更するワークロード グループを右クリックし、 **[プロパティ]**をクリックします。  
  
3.  **[リソース ガバナーのプロパティ]** ページで、自動的に **[リソース プールのワークロード グループ]** グリッドの対象ワークロード グループの行が選択されない場合は、その行を選択します。  
  
4.  変更する行のセルをクリックまたはダブルクリックし、新しい値を入力します。  
  
5.  変更を保存するには、 **[OK]**をクリックします。  
  
##  <a name="ChgWGTSQL"></a> Transact-SQL を使用してワークロード グループの設定を変更する  
 **Transact-SQL を使用してワークロード グループの設定を変更するには**  
  
1.  変更するプロパティ値を指定する ALTER WORKLOAD GROUP ステートメントを実行します。  
  
2.  ALTER RESOURCE GOVERNOR RECONFIGURE ステートメントを実行します。  
  
### <a name="example-transact-sql"></a>例 (Transact-SQL)  
 次の例では、 `groupAdhoc`という名前のワークロード グループに割り当てられたメモリ許可の割合の最大値を変更します。  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
WITH (REQUEST_MAX_MEMORY_GRANT_PERCENT = 30);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)   
 [ワークロード グループの作成](../../relational-databases/resource-governor/create-a-workload-group.md)   
 [リソース プールの作成](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [リソース プールの設定の変更](../../relational-databases/resource-governor/change-resource-pool-settings.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
