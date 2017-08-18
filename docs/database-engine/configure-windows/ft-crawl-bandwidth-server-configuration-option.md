---
title: "ft crawl bandwidth サーバー構成オプション | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- large memory buffers
- memory [SQL Server], buffers
- ft crawl bandwidth option
ms.assetid: e5864ad9-92f5-43b5-95de-46d68ded8694
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e582c59680c19f052ae10130d3673568b5eb60d6
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="ft-crawl-bandwidth-server-configuration-option"></a>ft crawl bandwidth サーバー構成オプション
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **ft crawl bandwidth** オプションを使用すると、大規模メモリ バッファーのプールを拡張するサイズを指定できます。 大規模メモリ バッファーのサイズは 4 MB です。 **max** パラメーターの値によって、大規模バッファー プールでフルテキスト メモリ マネージャーが保持する必要があるバッファーの最大数が指定されます。 **max** の値がゼロ (0) の場合、大規模バッファー プールで保持できるバッファー数に上限はありません。  
  
 **min** パラメーターによって、大規模メモリ バッファーのプールで保持する必要があるメモリ バッファーの最少数が指定されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ マネージャーからの要求時に、余分なバッファー プールがすべて解放されますが、このバッファーの最少数は保持されます。 ただし、 **min** の値にゼロ (0) が指定されている場合は、すべてのメモリ バッファーが解放されます。  
  
 特定の状況では、その時点で割り当てられるバッファーの数が **min** パラメーターによって指定された値よりも少なくなることがあります。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [ft notify bandwidth サーバー構成オプション](../../database-engine/configure-windows/ft-notify-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  

