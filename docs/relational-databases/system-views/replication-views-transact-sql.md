---
title: レプリケーションビュー (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
dev_langs:
- TSQL
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 51cc9434805fbd14204d74edae1594ae01c06bb2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68129565"
---
# <a name="replication-views-transact-sql"></a>レプリケーションビュー (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  これらのビューには、の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レプリケーションで使用される情報が含まれています。 ビューを使用すると、[レプリケーションシステムテーブル](../../relational-databases/system-tables/replication-tables-transact-sql.md)のデータに簡単にアクセスできます。 ビューは、データベースがパブリケーションまたはサブスクリプションデータベースとして有効になっている場合に、ユーザーデータベースに作成されます。 データベースがレプリケーショントポロジから削除されると、すべてのレプリケーションオブジェクトがユーザーデータベースから削除されます。 レプリケーションメタデータにアクセスするには、[レプリケーションストアドプロシージャ](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)を使用することをお勧めします。  
  
> [!IMPORTANT]  
>  システムビューは、ユーザーが直接変更することはできません。  
  
## <a name="replication-views"></a>レプリケーション ビュー  
 次に示すのは、レプリケーションで使用されるシステムビューの一覧で、データベースごとにグループ化されています。  
  
### <a name="replication-views-in-the-msdb-database"></a>msdb データベースのレプリケーション ビュー  
  
|||  
|-|-|  
|[MSdatatype_mappings &#40;Transact-sql&#41;](../../relational-databases/system-views/msdatatype-mappings-transact-sql.md)|[msdb.dbo.sysdatatypemappings &#40;Transact-sql&#41;](../../relational-databases/system-views/sysdatatypemappings-transact-sql.md)|  
  
### <a name="replication-views-in-the-distribution-database"></a>ディストリビューション データベースのレプリケーション ビュー  
  
|||  
|-|-|  
|[IHextendedArticleView &#40;Transact-sql&#41;](../../relational-databases/system-views/ihextendedarticleview-transact-sql.md)|[sysarticles &#40;システムビュー&#41; &#40;Transact-sql&#41;](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)|  
|[IHextendedSubscriptionView &#40;Transact-sql&#41;](../../relational-databases/system-views/ihextendedsubscriptionview-transact-sql.md)|[sysextendedarticlesview &#40;Transact-sql&#41;](../../relational-databases/system-views/sysextendedarticlesview-transact-sql.md)|  
|[IHsyscolumns &#40;Transact-sql&#41;](../../relational-databases/system-views/ihsyscolumns-transact-sql.md)|[syspublications &#40;システム ビュー&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-views/syspublications-system-view-transact-sql.md)|  
|[MSdistribution_status &#40;Transact-sql&#41;](../../relational-databases/system-views/msdistribution-status-transact-sql.md)|[syssubscriptions &#40;システム ビュー&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-views/syssubscriptions-system-view-transact-sql.md)|  
|[sysarticlecolumns &#40;システムビュー&#41; &#40;Transact-sql&#41;](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)||  
  
### <a name="replication-views-in-the-publication-database"></a>パブリケーションデータベースのレプリケーションビュー  
  
|||  
|-|-|  
|[sysmergeextendedarticlesview &#40;Transact-sql&#41;](../../relational-databases/system-views/sysmergeextendedarticlesview-transact-sql.md)|[sysmergepartitioninfoview &#40;Transact-sql&#41;](../../relational-databases/system-views/sysmergepartitioninfoview-transact-sql.md)|  
|[systranschemas &#40;Transact-sql&#41;](../../relational-databases/system-views/systranschemas-transact-sql.md)||  
  
### <a name="replication-views-in-the-subscription-database"></a>サブスクリプション データベースのレプリケーション ビュー  
  
|||  
|-|-|  
|[sysmergeextendedarticlesview &#40;Transact-sql&#41;](../../relational-databases/system-views/sysmergeextendedarticlesview-transact-sql.md)|[sysmergepartitioninfoview &#40;Transact-sql&#41;](../../relational-databases/system-views/sysmergepartitioninfoview-transact-sql.md)|  
|[systranschemas &#40;Transact-sql&#41;](../../relational-databases/system-views/systranschemas-transact-sql.md)||  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
