---
title: "トランザクション レプリケーションで使用するパブリケーションの種類 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactional replication, publications
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d2ce9609cb89baf0418449e2fd1b4d9bf1cd94c9
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="publication-types-for-transactional-replication"></a>トランザクション レプリケーションで使用するパブリケーションの種類
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  トランザクション レプリケーションでは、以下の 3 種類のパブリケーションが提供されます。  
  
|[パブリケーションの種類]|Description|  
|----------------------|-----------------|  
|標準トランザクション パブリケーション|サブスクライバーのデータがすべて読み取り専用であるトポロジに適したパブリケーションです (トランザクション レプリケーションでは、このパブリケーションがサブスクライバーで強制されるわけではありません)。<br /><br /> Transact-SQL またはレプリケーション管理オブジェクト (RMO) を使用する場合、標準トランザクション パブリケーションが既定で作成されます。 パブリケーションの新規作成ウィザードを使用する場合、 **[パブリケーションの種類]** ページで **[トランザクション パブリケーション]** を選択すると、標準トランザクション パブリケーションが作成されます。<br /><br /> パブリケーションの作成の詳細については、「 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)」を参照してください。|  
|ピア ツー ピア トポロジでのトランザクション パブリケーション|このパブリケーションの特徴として以下が挙げられます。<br /><br /> -各場所には同一のデータが格納され、パブリッシャーおよびサブスクライバーの両方の役割を果たします。<br /><br /> -同一の行は一度に 1 つの場所でのみ変更できます。<br /><br /> -これは、高可用性および読み取りのスケーラビリティが求められるサーバー環境に最適なトポロジです。<br /><br /> <br /><br /> 詳細については、「 [Peer-to-Peer Transactional Replication](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [トランザクション レプリケーション](../../../relational-databases/replication/transactional/transactional-replication.md)  
  
  
