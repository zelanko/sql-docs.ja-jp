---
title: external_library_files (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 07/24/2019
ms.prod: sql
ms.technology: machine-learning
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
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b2f1bbdc3936dc6295b9ecc51b937e50cae20670
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "80664227"
---
# <a name="sysexternal_library_files-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

外部ライブラリを構成するファイルごとに1行の情報を一覧表示します。

|列名 |データ型 |説明|
|------|------|-----|
|external_library_id | int |外部ライブラリオブジェクトの ID。 |
|コンテンツ |varbinary(max) |外部ライブラリファイルの成果物のコンテンツ。 |
|platform |tinyint |SQL Server がインストールされているホストプラットフォームの ID。 |
|platform_desc | nvarchar(60) |ホストプラットフォームの名前。 有効な値は ' WINDOWS '、' LINUX ' です。 |

### <a name="see-also"></a>関連項目  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[外部ライブラリの作成](../../t-sql/statements/create-external-library-transact-sql.md)  

