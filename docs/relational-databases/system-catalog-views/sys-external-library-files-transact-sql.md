---
title: sys.external_library_files (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 10/05/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- external_library_files
- external_library_files_TSQL
- sys.external_library_files
- sys.external_library_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_library_files catalog view
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a9666b58132feb79876c4e8074dc530440c05b2c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68220343"
---
# <a name="sysexternallibraryfiles-transact-sql"></a>sys.external_library_files (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

外部ライブラリを構成する各ファイルの行を一覧表示します。

|列名 |データ型 |説明|
|------|------|-----|
|external_library_id | ssNoversion |外部ライブラリ オブジェクトの ID。 |
|コンテンツ |varbinary(max) |外部ライブラリのファイル成果物のコンテンツ。 |
|プラットフォーム |TINYINT |SQL Server がインストールされているホスト プラットフォームの ID。 |
|platform_desc | nvarchar(60) |ホストのプラットフォームの名前です。 有効な値は、'WINDOWS'、'LINUX' です。 |

### <a name="see-also"></a>関連項目  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[外部ライブラリを作成します。](../../t-sql/statements/create-external-library-transact-sql.md)  
[SQL Server Machine Learning サービスのパッケージ管理](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
