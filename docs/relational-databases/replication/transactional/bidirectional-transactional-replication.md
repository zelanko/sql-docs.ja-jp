---
title: 双方向トランザクション レプリケーション | Microsoft Docs
description: 双方向トランザクション レプリケーションでは、2 台のサーバーで変更内容を交換しあうことができます。 各サーバーで、データのパブリッシュと、もう一方のサーバーからのパブリケーションのサブスクライブが行われます。
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: afd98116cd58e1e4c5fd3c284ea228d6c5ca6007
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2020
ms.locfileid: "86159420"
---
# <a name="bidirectional-transactional-replication"></a>双方向トランザクション レプリケーション
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/applies-to-version/sql-asdbmi.md)]
  双方向トランザクション レプリケーションとは、トランザクション レプリケーションの中でも特に、2 台のサーバーが互いに変更内容を交換し合うことのできるトポロジのことです。各サーバーはデータをパブリッシュすると共に、同じデータを含んだパブリケーションをもう一方のサーバーからサブスクライブします。 変更が確実にサブスクライバーに対してのみ送信され、サブスクライバーからパブリッシャーには送信されないようにするには、[sp_addsubscription &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) の `@loopback_detection` パラメーターを TRUE に設定します。  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降では、ピア ツー ピア トランザクション レプリケーションでもこのトポロジがサポートされますが、双方向レプリケーションを使用するとパフォーマンスが向上します。  
  
## <a name="see-also"></a>参照  
 [ピア ツー ピア トランザクション レプリケーション](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
