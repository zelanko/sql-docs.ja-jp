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
ms.technology: r-services
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
ms.openlocfilehash: a3196218bbb886544a77c2fd1184c806591b16e6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysexternallibraryfiles-transact-sql"></a>sys.external_library_files (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

外部ライブラリを構成する各ファイルの行を一覧表示します。

|列名 |データ型 |Description|
|------|------|-----|
|external_library_id | int |外部ライブラリ オブジェクトの ID。 |
|content |varbinary(max) |外部ライブラリ ファイル アイテムのコンテンツ。 |
|プラットフォーム |tinyint |SQL Server がインストールされているホストのプラットフォームの ID です。 |
|platform_desc | nvarchar(60) |ホストのプラットフォームの名前です。 有効な値は、'WINDOWS'、'LINUX' です。 |

### <a name="see-also"></a>参照  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[外部ライブラリを作成します。](../../t-sql/statements/create-external-library-transact-sql.md)  
[SQL Server マシン ラーニング サービス パッケージの管理](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
