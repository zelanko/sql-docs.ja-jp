---
title: external_library_files (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/25/2020
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
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 69c1b1c0f1ec2c7ab1c6cd17fbf949f0aaf166f2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754488"
---
# <a name="sysexternal_library_files-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

外部ライブラリを構成するファイルごとに1行の情報を一覧表示します。

|列名 |データ型 |説明|
|------|------|-----|
|external_library_id | INT |外部ライブラリオブジェクトの ID。 |
|コンテンツ |varbinary(max) |外部ライブラリファイルの成果物のコンテンツ。 |
|platform |tinyint |SQL Server がインストールされているホストプラットフォームの ID。 |
|platform_desc | nvarchar(60) |ホストプラットフォームの名前。 有効な値は ' WINDOWS '、' LINUX ' です。 |

### <a name="see-also"></a>関連項目  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[外部ライブラリの作成](../../t-sql/statements/create-external-library-transact-sql.md)  
