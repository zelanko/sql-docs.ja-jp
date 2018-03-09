---
title: "リソース正常性ポリシーの結果の表示 (SQL Server ユーティリティ) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: maintenance-plans
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80cb14fb-f4c6-4be2-ba17-eb4e4cddd35f
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b640be4a2da49c03c06b69b9e7d9c2ea4971e769
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="view-resource-health-policy-results-sql-server-utility"></a>リソース正常性ポリシーの結果の表示 (SQL Server ユーティリティ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスとデータ層アプリケーションに関する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのリソース パラメーターを表示するには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でユーティリティのダッシュボードを使用します。 詳細については、「 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)」を参照してください。  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="view-sql-server-utility-resource-health-policy-results"></a>SQL Server ユーティリティのリソース正常性ポリシーの結果の表示  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) で、 **[表示]**をクリックし、 **[ユーティリティ エクスプローラー]** をクリックして、ユーティリティ エクスプローラーのナビゲーション ウィンドウを表示します。 コンテンツ ウィンドウを表示するには、 **[表示]**をクリックし、 **[ユーティリティ エクスプローラーのコンテンツ]**をクリックします。  
  
2.  ナビゲーション ウィンドウで、**[ユーティリティへの接続]** ![](../../relational-databases/manage/media/connect-to-utility.gif "Connect_to_Utility") をクリックします。 ユーティリティ コントロール ポイント (UCP) を作成していない場合、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスまたはデータ層アプリケーションを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに登録していない場合は、「 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)」を参照してください。  
  
3.  UCP ノードをクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] マネージ インスタンスおよびデータ層アプリケーションの概要データを表示します (更新するには右クリックします)。 ダッシュボードのデータは、コンテンツ ウィンドウに表示されます。  
  
4.  **[マネージ インスタンス]** ノードをクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] マネージ インスタンスのリスト ビュー データを表示します (更新するには右クリックします)。 リスト ビューのデータは、コンテンツ ウィンドウに表示されます。  
  
5.  **[配置済みのデータ層アプリケーション]** ノードをクリックし、データ層アプリケーションのリスト ビュー データを表示します (更新するには右クリックします)。 リスト ビューのデータは、コンテンツ ウィンドウに表示されます。  
  
## <a name="see-also"></a>参照  
 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;](../../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)   
 [配置済みのデータ層アプリケーションの詳細 &#40;SQL Server ユーティリティ&#41;](http://msdn.microsoft.com/library/79c41dd9-abcb-434e-9326-00a341d5c867)   
 [マネージ インスタンスの詳細 &#40;SQL Server ユーティリティ&#41;](http://msdn.microsoft.com/library/6e51b7bb-a733-4852-8c33-7f4dbdf931c2)   
 [ユーティリティの管理 &#40;SQL Server ユーティリティ&#41;](http://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d)  
  
  
