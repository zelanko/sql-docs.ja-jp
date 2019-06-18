---
title: MSSQLSERVER_3156 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3156 (Database Engine error)
ms.assetid: 345d8ed4-177e-4ec3-bab3-25d30000e323
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b10bd409a52708e69ef9ae3ad8cf629d73b446dd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62645075"
---
# <a name="mssqlserver3156"></a>MSSQLSERVER_3156
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
