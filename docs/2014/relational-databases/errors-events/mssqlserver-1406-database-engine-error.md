---
title: MSSQLSERVER_1406 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1406 (Database Engine error)
ms.assetid: 915f97de-9b74-41f8-8bd5-b2d061416718
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e823c14fcb6e1a408d1589d0588a3fb966552d7
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967952"
---
# <a name="mssqlserver_1406"></a>MSSQLSERVER_1406
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1406|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBM_BADSTATEFORFORCESERVICE|  
|メッセージ テキスト|サービスを安全に実行できません。 アクセスできるようにするには、データベース ミラーリングを削除して、データベース "%.*ls" を復旧してください。|  
  
## <a name="explanation"></a>説明  
 ミラーリング状態ではサービスを強制するプロセスが正しく動作することを保証できないため、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]でサービスを強制できません。  
  
## <a name="user-action"></a>ユーザーの操作  
 データベース ミラーリングを削除します。 その後、ミラー データベースを復旧して、このデータベースにアクセスできるようにします。  
  
## <a name="see-also"></a>参照  
 [データベースミラーリングセッションでのサービスの強制 Transact-sql&#41;の &#40;](../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)   
 [データベース ミラーリングの削除 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
