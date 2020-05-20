---
title: Filestream および FileTable の動的管理ビュー (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- FileTables [SQL Server], dynamic management views
ms.assetid: e50a135d-6644-42a4-a0df-1c7a2b722051
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 216cbfbfd1357298d4b816838fd8bfa5428a65f8
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829516"
---
# <a name="filestream-and-filetable-dynamic-management-views-transact-sql"></a>Filestream および FileTable の動的管理ビュー (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ここでは、FILESTREAM 機能および FileTable 機能に関連する動的管理ビューについて説明します。  
  
## <a name="filestream-dynamic-management-views-and-functions"></a>Filestream 動的管理ビューおよび関数  
 [sys.dm_filestream_file_io_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-handles-transact-sql.md)  
 現在開いているトランザクション ファイル ハンドルを表示します。  
  
 [sys.dm_filestream_file_io_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-requests-transact-sql.md)  
 現在のファイル入力とファイル出力の要求を表示します。  
  
## <a name="filetable-dynamic-management-views-and-functions"></a>FileTable 動的管理ビューおよび関数  
 [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md)  
 現在開いている、FileTable データに対する非トランザクション ファイル ハンドルを表示します。  

## <a name="see-also"></a>参照
[ストリーム](../../relational-databases/blob/filestream-sql-server.md)
<br>[Filetable](../../relational-databases/blob/filetables-sql-server.md)
<br>[Filestream および FileTable のカタログ ビュー (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
<br>[Filestream および FileTable システムストアドプロシージャ (Transact-sql)](../system-stored-procedures/filestream-and-filetable-system-stored-procedures.md)
  
