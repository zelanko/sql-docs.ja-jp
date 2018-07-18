---
title: MSSQLSERVER_7915 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4f092add04bdc57cb76ed3770122aa889074698c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419931"
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
  
  
