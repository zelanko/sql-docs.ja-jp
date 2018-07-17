---
title: 双方向トランザクション レプリケーション | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
caps.latest.revision: 27
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7adb719f32533fe28a21bcd092e8c7b5bf593918
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351384"
---
# <a name="bidirectional-transactional-replication"></a>双方向トランザクション レプリケーション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  双方向トランザクション レプリケーションとは、トランザクション レプリケーションの中でも特に、2 台のサーバーが互いに変更内容を交換し合うことのできるトポロジのことです。各サーバーはデータをパブリッシュすると共に、同じデータを含んだパブリケーションをもう一方のサーバーからサブスクライブします。 変更がサブスクライバーに対してのみ送信され、サブスクライバーからパブリッシャーには送信されないようにするには、[sp_addsubscription &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) の **@loopback_detection** パラメーターを TRUE に設定します。  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降では、ピア ツー ピア トランザクション レプリケーションでもこのトポロジがサポートされますが、双方向レプリケーションを使用するとパフォーマンスが向上します。  
  
## <a name="see-also"></a>参照  
 [@loopback_detection](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
