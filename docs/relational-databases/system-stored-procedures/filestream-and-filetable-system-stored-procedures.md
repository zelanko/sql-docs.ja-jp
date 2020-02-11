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
ms.openlocfilehash: 1ebcaf4659d7be880f0f0e901b2eadcc9002b2d9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67942247"
---
# <a name="filestream-and-filetable-system-stored-procedures-transact-sql"></a>Filestream および FileTable システムストアドプロシージャ (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  ここでは、FileTable および Filestream 機能に対するシステムストアドプロシージャについて説明します。  

## <a name="filestream-and-filetable-system-stored-procedures"></a>Filestream および Filetable システムストアドプロシージャ
  [sp_filestream_force_garbage_collection (Transact-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)

   FILESTREAM ガベージコレクターを強制的に実行し、不要な FILESTREAM ファイルを削除します。

  [sp_kill_filestream_non_transacted_handles (Transact-sql)](filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md)

  FileTable データに対する非トランザクション ファイル ハンドルを閉じます。


## <a name="see-also"></a>参照
[Filestream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Filetable](../../relational-databases/blob/filetables-sql-server.md)
<br>[Filestream および FileTable の動的管理ビュー (Transact-sql)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[Filestream および FileTable のカタログビュー (Transact-sql)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
  
  
