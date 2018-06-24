---
title: MSSQLSERVER_1406 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 1406 (Database Engine error)
ms.assetid: 915f97de-9b74-41f8-8bd5-b2d061416718
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 259d6e37f0798cfacaac39c89dec091053c16c57
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074413"
---
# <a name="mssqlserver1406"></a>MSSQLSERVER_1406
    
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
 [データベース ミラーリング セッションでのサービスの強制 &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)   
 [データベース ミラーリングの削除 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  