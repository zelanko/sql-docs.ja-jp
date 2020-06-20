---
title: MSSQLSERVER_2516 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7e356b3de7ce46ae64d2d94461eed16b2d36baa6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85034426"
---
# <a name="mssqlserver_2516"></a>MSSQLSERVER_2516
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2516|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_REPAIR_DIFF_MAP_INVALIDATED|  
|メッセージ テキスト|修復により、データベース NAME の差分ビットマップが無効になりました。 差分バックアップ チェーンが壊れています。 データベース全体をバックアップしてから、差分バックアップを実行できます。|  
  
## <a name="explanation"></a>説明  
 この情報メッセージは、エラー MSSQLEngine_2515 の修復時に返されます。  
  
## <a name="user-action"></a>ユーザーの操作  
 データベースの完全バックアップを実行します。  
  
## <a name="see-also"></a>参照  
 [データベースの完全バックアップの作成 &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
  
