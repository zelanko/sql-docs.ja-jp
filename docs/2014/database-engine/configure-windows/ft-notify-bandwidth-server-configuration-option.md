---
title: ft notify bandwidth サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- ft notify bandwidth opion
- small memory buffers
- memory [SQL Server], buffers
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 375e7c8a1bb520f5a3004c5279682d5b3f145b13
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62782497"
---
# <a name="ft-notify-bandwidth-server-configuration-option"></a>ft notify bandwidth サーバー構成オプション
  
  **ft notify bandwidth** オプションは、小規模メモリ バッファーのプールの最大サイズを指定する際に使用します。 小規模メモリ バッファーのサイズは 64 KB です。 
  *max* パラメーターの値によって、小規模バッファー プールでフルテキスト メモリ マネージャーが保持する必要があるバッファーの最大数が指定されます。 `max`値が0の場合、小さいバッファープールに格納できるバッファー数に上限はありません。  
  
 
  **min** パラメーターによって、小規模メモリ バッファーのプールで保持する必要があるメモリ バッファーの最少数が指定されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリマネージャーから[!INCLUDE[msCoName](../../includes/msconame-md.md)]の要求時に、余分なバッファープールがすべて解放されますが、このバッファーの最小数が維持されます。 ただし、 **min** の値にゼロ (0) が指定されている場合は、すべてのメモリ バッファーが解放されます。  
  
 特定の状況下では、現在割り当てられているバッファーの数が**min**パラメーターによって指定された値よりも小さくなっています。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [ft クロール帯域幅サーバー構成オプション](ft-crawl-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
