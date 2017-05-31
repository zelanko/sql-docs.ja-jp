---
title: "SQL Server の Columnstore オブジェクト | Microsoft Docs"
ms.custom: 
ms.date: 04/12/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae663a49-012f-4ffe-a332-f03157843052
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 418dddd9e87b490170b6d07c03d93a6eea912edf
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-columnstore-object"></a>SQL Server の Columnstore オブジェクト
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  **SQLServer:Columnstore** オブジェクトは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で列ストア インデックスの実行を監視するカウンターを提供します。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Columnstore** カウンターについて説明します。  
  
|Columnstore カウンター|説明|  
|--------------------------|-----------------|  
|**閉じられたデルタ行グループ数**|閉じられたデルタ行グループの数。|  
|**圧縮されたデルタ行グループ数**|圧縮されたデルタ行グループの数。|  
|**作成されたデルタ行グループ数**|作成されたデルタ行グループの数。|  
|**セグメント キャッシュ ヒット率**|ディスクから読み取らずに、columnstore プール内で見つかった列セグメントのパーセンテージ。|  
|**セグメント キャッシュ ヒット率ベース**|内部使用のみです。|
|**セグメント読み取り数/秒**|物理セグメント読み取りの発生回数。|  
|**削除バッファーの合計移行回数**|組ムーバーが削除バッファーをクリーンアップした回数。|  
|**マージ ポリシーの合計評価数**|columnstore のマージ ポリシーを評価した回数。|  
|**圧縮された行グループ合計数**|圧縮された行グループの合計数。|  
|**マージに適した行グループ合計数**|SQL Server の開始以降 MERGE に適したソースの行グループ数。|  
|**マージと圧縮が行われた行グループ合計数**|SQL Server の起動以降に MERGE で作成された圧縮ターゲット行グループの数。|  
|**マージされたソース行グループ合計数**|SQL Server の起動以降にマージされたソース行グループの数。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  

