---
title: Filestream と FileTable のシステム ストアド プロシージャ (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- FileTables [SQL Server], catalog views
ms.assetid: 2c83a4a7-720b-4435-a3b5-788c29f56949
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4d7df9111622f1674ecc677a7b2dcd7d22ae564b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="filestream-and-filetable-system-stored-procedures-transact-sql"></a>Filestream および FileTable のシステム ストアド プロシージャ (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このセクションでは、FileTable と Filestream 機能に、システム ストアド プロシージャについて説明します。  

## <a name="filestream-and-filetable-system-stored-procedures"></a>Filestream および Filetable のシステム ストアド プロシージャ
  [sp_filestream_force_garbage_collection (TRANSACT-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)

   FILESTREAM ガベージ コレクターを強制的に実行して、不要な FILESTREAM ファイルを削除します。

  [sp_kill_filestream_non_transacted_handles (TRANSACT-SQL)](filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md)

  FileTable データに対する非トランザクション ファイル ハンドルを閉じます。


## <a name="see-also"></a>参照
[Filestream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Filetable](../../relational-databases/blob/filetables-sql-server.md)
<br>[Filestream および FileTable 動的管理ビュー (TRANSACT-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[Filestream および FileTable のカタログ ビュー (TRANSACT-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
  
  
