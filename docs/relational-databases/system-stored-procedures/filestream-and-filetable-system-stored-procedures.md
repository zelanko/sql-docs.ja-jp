---
title: Filestream および FileTable システムストアドプロシージャ (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- FileTables [SQL Server], catalog views
ms.assetid: 2c83a4a7-720b-4435-a3b5-788c29f56949
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e0c7697c6c65f6d39de4d5f52ea2fdb85ea4e218
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731792"
---
# <a name="filestream-and-filetable-system-stored-procedures-transact-sql"></a>Filestream および FileTable システム ストアド プロシージャ (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  ここでは、FileTable および Filestream 機能に対するシステムストアドプロシージャについて説明します。  

## <a name="filestream-and-filetable-system-stored-procedures"></a>Filestream および Filetable システムストアドプロシージャ
  [sp_filestream_force_garbage_collection (Transact-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)

   FILESTREAM ガベージコレクターを強制的に実行し、不要な FILESTREAM ファイルを削除します。

  [sp_kill_filestream_non_transacted_handles (Transact-sql)](filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md)

  FileTable データに対する非トランザクション ファイル ハンドルを閉じます。


## <a name="see-also"></a>関連項目
[FileStream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Filetable](../../relational-databases/blob/filetables-sql-server.md)
<br>[Filestream および FileTable の動的管理ビュー (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[Filestream および FileTable のカタログ ビュー (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
  
  
