---
title: "[メンテナンス プラン]([サーバー]) | Microsoft Docs"
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
f1_keywords:
- sql13.swb.maint.servers.f1
- sql13.swb.maint.maintplanproperties.server.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cb602533a9ce853c59daa501a84dbae206127c40
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="maintenance-plan-servers"></a>[メンテナンス プラン] \([サーバー])
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **[サーバー]** ダイアログ ボックスでは、メンテナンス プランを実行するサーバーを選択します。  
  
 1 台のマスター サーバーと 1 台以上の対象サーバーで構成されたマルチサーバー環境は、マルチサーバー メンテナンス プランを作成するように構成する必要があります。 マルチサーバー メンテナンス プランでは、ローカル サーバーをマスター サーバーとして構成する必要があります。 マルチサーバー環境では、" **(local)** " マスター サーバーと対応するすべての対象サーバーがこのダイアログ ボックスに表示されます。 ローカル サーバーに対して 1 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブが作成されます。 このジョブが有効かどうかは、" **(local)** " サーバーを選択するかどうかによって決まります。 対象サーバーを選択すると、マルチサーバー ジョブが作成され、選択した各対象サーバーにダウンロードされます。 対象サーバーを選択しない場合、マルチサーバー ジョブは削除されます。  
  
## <a name="see-also"></a>参照  
 [メンテナンス プラン](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [マルチサーバー環境の作成](http://msdn.microsoft.com/library/edc2b60d-15da-40a1-8ba3-f1d473366ee6)   
 [マスター サーバーの作成](http://msdn.microsoft.com/library/05739a73-1fdf-4d9d-92a6-70f328380322)   
 [対象サーバーの作成](http://msdn.microsoft.com/library/13aabe2d-67fe-4c67-8d49-2928dd705b7a)  
  
  
