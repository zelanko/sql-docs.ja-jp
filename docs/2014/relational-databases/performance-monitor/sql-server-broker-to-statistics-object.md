---
title: 'SQL Server: Broker TO Statistics オブジェクト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Broker Transmission Object object
- 'SQL Server: Broker Transmission Object'
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 38a8860fb4bb405586a5e1c0e6756d8a1d0a12d3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074175"
---
# <a name="sql-server-broker-to-statistics-object"></a>SQL Server: Broker TO Statistics オブジェクト
  SQLServer:Broker TO Statistics パフォーマンス オブジェクトは、[!INCLUDE[ssSB](../../includes/sssb-md.md)] ダイアログが転送オブジェクトを要求した回数、および転送オブジェクトが **tempdb** に書き込まれた頻度に関する情報を報告します。  
  
 転送オブジェクトには、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] ダイアログのメッセージ転送状態が記録されます。 このオブジェクトはメモリに格納されます。 メモリを解放するために、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] は非アクティブな転送オブジェクトのバッチを定期的に **tempdb**内の作業テーブルに書き込みます。  
  
 次の表は、このオブジェクトに含まれているカウンターの一覧です。  
  
|SQL Server Broker TO Statistics カウンター|説明|  
|----------------------------------------------|-----------------|  
|**平均Length of Batched Writes**|バッチに保存される転送オブジェクトの平均数。|  
|**平均Time To Write Batch (ms)**|転送オブジェクトのバッチを保存するために必要な平均時間 (ミリ秒)。|  
|**平均Time Between Batches (ms)**|転送オブジェクトのバッチが書き込まれる時間間隔の平均値 (ミリ秒)。|  
|**Tran Object Gets/sec**|ダイアログが転送オブジェクトを要求した 1 秒あたりの回数。|  
|**Tran Objects Marked Dirty/sec**|転送オブジェクトがダーティとマークされた 1 秒あたりの回数。 最初の変更でメモリ内のコピーが **tempdb**に格納されているコピーと同一でなくなると、転送オブジェクトがダーティとマークされます。 転送オブジェクトは、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] がダイアログのメッセージ転送状態の変化を記録する必要がある場合に変更されます。|  
|**Tran Object Writes/sec**|転送オブジェクトのバッチが **tempdb** の作業テーブルに書き込まれた 1 秒あたりの回数。 書き込み回数が多い場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメモリに負荷がかかっている可能性があります。|  
  
## <a name="see-also"></a>参照  
 [SQL Server の Access Methods オブジェクト](sql-server-access-methods-object.md)   
 [SQL Server: Memory Manager オブジェクト](sql-server-memory-manager-object.md)   
 [リソースの利用状況の監視 &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  