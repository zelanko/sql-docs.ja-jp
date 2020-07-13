---
title: MSSQLSERVER_1406 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1406 (Database Engine error)
ms.assetid: 915f97de-9b74-41f8-8bd5-b2d061416718
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d230613e3c972f8faedbc044c11fdd5c5c835e37
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781051"
---
# <a name="mssqlserver_1406"></a>MSSQLSERVER_1406
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
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
[データベース ミラーリング セッションでのサービスを強制する &#40;Transact-SQL&#41;](~/database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)  
[データベース ミラーリングの削除 &#40;SQL Server&#41;](~/database-engine/database-mirroring/removing-database-mirroring-sql-server.md)  
  
