---
title: SQL Server の XTP ストレージ | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 502ee4eb72f476d3e63eee6efbe2aaa21df88d75
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2018
ms.locfileid: "53379743"
---
# <a name="sql-server-xtp-storage"></a>SQL Server の XTP ストレージ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  SQL Server XTP ストレージのパフォーマンス オブジェクトには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインメモリ OLTP のためのオンディスク ストレージに関連するカウンターが含まれています。  
  
 次の表では、 **SQL Server XTP ストレージ** カウンターについて説明します。  
  
|カウンター|[説明]|  
|-------------|-----------------|  
|**終了したチェックポイント**|オンライン エージェントによって終了されたチェックポイントの数。|  
|**完了したチェックポイント**|オフライン チェックポイント スレッドによって処理されたチェックポイントの数。|  
|**完了したコア マージ**|マージ ワーカー スレッドによって実行されたコア マージの数。 これらのマージは、引き続きインストールされている必要があります。|  
|**マージ ポリシーの評価**|サーバーが開始してから行われたマージ ポリシーの評価の数。|  
|**未処理のマージ要求**|サーバーが開始してから未処理になっているのマージ要求の数。|  
|**放棄されたマージ**|エラーにより放棄されたマージの数。|  
|**インストールされているマージ**|適切にインストールされたマージの数。|  
|**マージされているファイルの総数**|マージされているソース ファイルの総数。 この数を使用すると、マージ内のソース ファイル数の平均がわかります。|  
  
## <a name="see-also"></a>参照  
 [SQL Server XTP &#40;インメモリ OLTP&#41; パフォーマンス カウンター](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
