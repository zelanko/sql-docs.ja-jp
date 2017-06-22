---
title: MSSQLSERVER_3156 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 3156 (Database Engine error)
ms.assetid: 345d8ed4-177e-4ec3-bab3-25d30000e323
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 08f8ea872ef58a42b07254417db0a19a5dfd9fd7
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver3156"></a>MSSQLSERVER_3156
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|3156|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|LDDB_CANT_WRITE|  
|メッセージ テキスト|ファイル '%ls' を '%ls' に復元できません。 WITH MOVE を使用して、そのファイルにとって有効な場所を特定してください。|  
  
## <a name="explanation"></a>説明  
この一般的なメッセージは、指定の場所に問題があり、ファイルを復元できなかった場合の論理ファイル名または物理ファイル名を示すものです。  
  
### <a name="possible-causes"></a>考えられる原因  
以下のような原因が考えられます。  
  
-   指定の Windows ディレクトリへのアクセス権が必要。  
  
-   パスの入力ミス、または存在しないパスを指定した。  
  
-   ファイル名が別のファイルで使用されており、上書きできない。  
  
## <a name="user-action"></a>ユーザーの操作  
エラー ログで、他のメッセージに詳細がないか確認します。  
  
アクセス権を付与するなどして指定場所の問題を修正するか、RESTORE ステートメントで WITH MOVE オプションを使用してファイルを再配置します。  
  
## <a name="see-also"></a>参照  
[データベースを新しい場所に復元する &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[新しい場所へのファイルの復元 &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
  

