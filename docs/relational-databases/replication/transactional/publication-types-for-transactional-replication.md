---
title: "トランザクション レプリケーションで使用するパブリケーションの種類 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactional replication, publications
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3bfa3cae7f71edbae561b3d2ab1eb7784a433df6
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="publication-types-for-transactional-replication"></a>トランザクション レプリケーションで使用するパブリケーションの種類
  トランザクション レプリケーションでは、以下の 3 種類のパブリケーションが提供されます。  
  
|[パブリケーションの種類]|説明|  
|----------------------|-----------------|  
|標準トランザクション パブリケーション|サブスクライバーのデータがすべて読み取り専用であるトポロジに適したパブリケーションです (トランザクション レプリケーションでは、このパブリケーションがサブスクライバーで強制されるわけではありません)。<br /><br /> Transact-SQL またはレプリケーション管理オブジェクト (RMO) を使用する場合、標準トランザクション パブリケーションが既定で作成されます。 パブリケーションの新規作成ウィザードを使用する場合、 **[パブリケーションの種類]** ページで **[トランザクション パブリケーション]** を選択すると、標準トランザクション パブリケーションが作成されます。<br /><br /> パブリケーションの作成の詳細については、「 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)」を参照してください。|  
|ピア ツー ピア トポロジでのトランザクション パブリケーション|このパブリケーションの特徴として以下が挙げられます。<br /><br /> -各場所には同一のデータが格納され、パブリッシャーおよびサブスクライバーの両方の役割を果たします。<br /><br /> -同一の行は一度に 1 つの場所でのみ変更できます。<br /><br /> -これは、高可用性および読み取りのスケーラビリティが求められるサーバー環境に最適なトポロジです。<br /><br /> <br /><br /> 詳細については、「 [Peer-to-Peer Transactional Replication](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [トランザクション レプリケーション](../../../relational-databases/replication/transactional/transactional-replication.md)  
  
  
