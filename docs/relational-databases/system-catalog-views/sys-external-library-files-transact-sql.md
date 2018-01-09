---
title: "sys.external_library_files (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- external_library_files
- external_library_files_TSQL
- sys.external_library_files
- sys.external_library_files_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.external_library_files catalog view
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: a03a50bdeda18d027fbad56e2cd4b86a261052b7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="sysexternallibraryfiles-transact-sql"></a>sys.external_library_files (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

外部ライブラリを構成する各ファイルの行を一覧表示します。

|列名 |データ型 |Description|
|------|------|-----|
|external_library_id | ssNoversion |外部ライブラリ オブジェクトの ID。 |
|content |varbinary(max) |外部ライブラリ ファイル アイテムのコンテンツ。 |
|プラットフォーム |TINYINT |SQL Server がインストールされているホストのプラットフォームの ID です。 |
|platform_desc | nvarchar(60) |ホストのプラットフォームの名前です。 有効な値は、'WINDOWS'、'LINUX' です。 |

### <a name="see-also"></a>参照  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[外部ライブラリを作成します。](../../t-sql/statements/create-external-library-transact-sql.md)  
[SQL Server マシン ラーニング サービス パッケージの管理](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
