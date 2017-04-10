---
title: "双方向トランザクション レプリケーション | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "双方向のレプリケーション"
  - "トランザクション レプリケーション, 双方向のレプリケーション"
  - "双方向トランザクション レプリケーション"
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 27
---
# 双方向トランザクション レプリケーション
  双方向トランザクション レプリケーションとは、トランザクション レプリケーションの中でも特に、2 台のサーバーが互いに変更内容を交換し合うことのできるトポロジのことです。各サーバーはデータをパブリッシュすると共に、同じデータを含んだパブリケーションをもう一方のサーバーからサブスクライブします。  **@Loopback_detection** のパラメーター [sp_addsubscription & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) 変更がサブスクライバーに送信のみと、パブリッシャーに送信される変更が発生しないことを確認を TRUE に設定されます。  
  
  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] し、以降のバージョンでは、でも、このトポロジはピア ツー ピアのトランザクション レプリケーションでサポートされますが、双方向のレプリケーションは、パフォーマンスの向上を提供できます。  
  
## 参照  
 [ピア ツー ピア トランザクション レプリケーション](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  