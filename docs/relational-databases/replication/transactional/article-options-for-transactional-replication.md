---
title: "トランザクション レプリケーションのアーティクル オプション | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
caps.latest.revision: "30"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d86aa0fec11f31db656716f3a043cf9faf396584
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="article-options-for-transactional-replication"></a>トランザクション レプリケーションのアーティクル オプション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] トランザクション パブリケーションには、アーティクルのためのオプションがいくつかあります。 たとえば、トランザクション レプリケーションでは次のようなことが可能です。  
  
-   パブリッシャーからサブスクライバーに変更を反映する方法を指定できます。 詳細については、「[トランザクション アーティクルに変更を反映する方法の指定](../../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)」を参照してください。  
  
-   ストアド プロシージャの実行をレプリケートするように指定できます。 これは、大量のデータに影響を与えるメンテナンス用ストアド プロシージャの結果をレプリケートする場合に便利です。 詳細については、「 [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)」を参照してください。  
  
-   制約やトリガーをサブスクライバーにコピーするかどうかなど、スキーマ オプションを指定します。 詳細については、「 [スキーマ オプションの指定](../../../relational-databases/replication/publish/specify-schema-options.md)」を参照してください。  
  
-   行フィルターや列フィルターを使用できます。 テーブル アーティクルをフィルター選択すると、パブリッシュされるデータのパーティションを作成できます。 詳細については、「[パブリッシュされたデータのフィルター処理](../../../relational-databases/replication/publish/filter-published-data.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
