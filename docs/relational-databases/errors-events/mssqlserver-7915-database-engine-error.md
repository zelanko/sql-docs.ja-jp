---
title: MSSQLSERVER_7915 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: b0b8d1752a64451824195426c241d19472483570
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver7915"></a>MSSQLSERVER_7915
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|7915|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC2_REPAIR_IAM_CHAIN_REBUILT|  
|メッセージ テキスト|修復 : オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) の IAM チェーンがページ P_ID の前で切り捨てられました。チェーンが再構築されます。|  
  
## <a name="explanation"></a>説明  
これは、REPAIR から送られた情報メッセージであり、指定の IAM (Index Allocation Map) チェーンが再構築できるように修復されたことを示します。 この修復で、IAM チェーンの新しい開始位置の割り当てや、チェーンからの不正なページの削除が必要であった可能性があります。  
  
## <a name="user-action"></a>ユーザーの操作  
なし  
  
