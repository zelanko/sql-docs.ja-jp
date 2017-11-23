---
title: "レプリケーション ビュー (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: TSQL
helpviewer_keywords:
- distribution databases [SQL Server replication], system views
- metadata [SQL Server], views
- views [SQL Server], replication
- replication views [SQL Server]
- publications [SQL Server replication], system views
- articles [SQL Server replication], system views
- replication metadata [SQL Server]
- subscriptions [SQL Server replication], system views
- system views [SQL Server], replication
ms.assetid: 93e5056d-0d93-4a48-ba33-72762eb995d8
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b73dfed7709b76d20856fe03648a7e0c6db0d258
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="replication-views-transact-sql"></a>レプリケーション ビュー (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  これらのビューには、レプリケーションで使用される情報が含まれて[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 ビュー内のデータに簡単にアクセスを有効にする[レプリケーション システム テーブル](../../relational-databases/system-tables/replication-tables-transact-sql.md)です。 データベースがパブリケーション データベースまたはサブスクリプション データベースとして有効な場合に、ビューはユーザー データベースで作成されます。 データベースがレプリケーション トポロジから削除されると、すべてのレプリケーション オブジェクトはユーザー データベースから削除されます。 使用してレプリケーション メタデータにアクセスするための推奨される方法は、[レプリケーションのストアド プロシージャ](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)です。  
  
> [!IMPORTANT]  
>  ユーザーはシステム ビューを直接変更しないでください。  
  
## <a name="replication-views"></a>レプリケーション ビュー  
 次に、レプリケーションで使用するシステム ビューの一覧を、データベースごとにグループ化して示します。  
  
### <a name="replication-views-in-the-msdb-database"></a>msdb データベースのレプリケーション ビュー  
  
|||  
|-|-|  
|[MSdatatype_mappings &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/msdatatype-mappings-transact-sql.md)|[sysdatatypemappings &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/sysdatatypemappings-transact-sql.md)|  
  
### <a name="replication-views-in-the-distribution-database"></a>ディストリビューション データベースのレプリケーション ビュー  
  
|||  
|-|-|  
|[IHextendedArticleView &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/ihextendedarticleview-transact-sql.md)|[sysarticles &#40;です。システム ビュー &#41;&#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)|  
|[IHextendedSubscriptionView &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/ihextendedsubscriptionview-transact-sql.md)|[sysextendedarticlesview &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/sysextendedarticlesview-transact-sql.md)|  
|[IHsyscolumns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/ihsyscolumns-transact-sql.md)|[syspublications &#40;システム ビュー&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-views/syspublications-system-view-transact-sql.md)|  
|[MSdistribution_status &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/msdistribution-status-transact-sql.md)|[syssubscriptions &#40;システム ビュー&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-views/syssubscriptions-system-view-transact-sql.md)|  
|[sysarticlecolumns &#40;です。システム ビュー &#41;&#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)||  
  
### <a name="replication-views-in-the-publication-database"></a>パブリケーション データベースのレプリケーション ビュー  
  
|||  
|-|-|  
|[sysmergeextendedarticlesview &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/sysmergeextendedarticlesview-transact-sql.md)|[sysmergepartitioninfoview &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/sysmergepartitioninfoview-transact-sql.md)|  
|[systranschemas &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/systranschemas-transact-sql.md)||  
  
### <a name="replication-views-in-the-subscription-database"></a>サブスクリプション データベースのレプリケーション ビュー  
  
|||  
|-|-|  
|[sysmergeextendedarticlesview &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/sysmergeextendedarticlesview-transact-sql.md)|[sysmergepartitioninfoview &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/sysmergepartitioninfoview-transact-sql.md)|  
|[systranschemas &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/systranschemas-transact-sql.md)||  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
