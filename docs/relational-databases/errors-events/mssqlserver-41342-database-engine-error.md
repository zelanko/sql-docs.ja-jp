---
title: MSSQLSERVER_41342 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e2e8136363205cf06a210f8a741ed8eb8debaaeb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63046327"
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
|メッセージ テキスト|システムのプロセッサのモデルは、*construct* の作成をサポートしません。 このエラーは通常、古いプロセッサで発生します。|  
  
## <a name="explanation"></a>説明  
メモリ最適化テーブルには、128 ビット値のアトミックな compare-and-exchange 操作をサポートするプロセッサ モデルが必要であり、これにはアセンブリ命令 CMPXCHG16B が必要です。 特定の古い AMD プロセッサ モデルでは、CMPXCHG16B 命令がサポートされていません。 また、特定の仮想化環境では、既定でこの命令が有効になっていません。  
  
## <a name="user-action"></a>ユーザーの操作  
プロセッサをアップグレードします。 プロセッサで命令がサポートされていて、仮想マシンで SQL Server を実行している場合は、命令 CMPXCHG16B をサポートするように構成を変更してください。  
  
## <a name="see-also"></a>参照  
[インメモリ OLTP &#40;インメモリ最適化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
