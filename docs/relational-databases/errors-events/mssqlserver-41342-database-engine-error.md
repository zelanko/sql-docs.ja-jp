---
title: MSSQLSERVER_41342 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3d3dc1d6bff5855b5aff6bbd36d08bcde3ccc828
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver41342"></a>MSSQLSERVER_41342
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|41342|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|HK_HW_NOT_SUPPORTED|  
|メッセージ テキスト|システムのプロセッサのモデルは、*construct* の作成をサポートしません。 このエラーは通常、古いプロセッサで発生します。 サポートされているモデルについては、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックを参照してください。|  
  
## <a name="explanation"></a>説明  
メモリ最適化テーブルには、128 ビット値のアトミックな compare-and-exchange 操作をサポートするプロセッサ モデルが必要であり、これにはアセンブリ命令 CMPXCHG16B が必要です。 特定の古い AMD プロセッサ モデルでは、CMPXCHG16B 命令がサポートされていません。 また、特定の仮想化環境では、既定でこの命令が有効になっていません。  
  
## <a name="user-action"></a>ユーザーの操作  
プロセッサをアップグレードします。 プロセッサで命令がサポートされていて、仮想マシンで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行している場合は、命令 CMPXCHG16B をサポートするように構成を変更してください。  
  
## <a name="see-also"></a>参照  
[インメモリ OLTP &#40;インメモリ最適化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
