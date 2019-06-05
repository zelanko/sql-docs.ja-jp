---
title: sys.sql_feature_restrictions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/20/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sql_sql_feature_restrictions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_feature_restrictions catalog view
author: vainolo
ms.author: arib
manager: tomerw
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 9ffdcaaefe60c1972993501814cae555fb907f26
ms.sourcegitcommit: 561cee96844b82ade6cf543a228028ad5c310768
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66507000"
---
# <a name="syssqlfeaturerestrictions-transact-sql"></a>sys.sql_feature_restrictions (TRANSACT-SQL)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

データベース内のすべての制限の 1 つの行を返します。
  
| 列名 | データ型 | 説明 |
|-------------|-----------|-------------|
| class       | nvarchar(128) | 制限が適用されるオブジェクトのクラス |
| オブジェクト      | nvarchar (256) | 制限が適用されるオブジェクトの名前 |
| 機能     | nvarchar(128) | 制限されている機能 |
  
## <a name="remarks"></a>コメント

現在、次の機能を制限できます。

| 機能          | 説明 |
|------------------|-------------|
| N'ErrorMessages' | 制限されているときにエラー メッセージ内の任意のユーザー データがマスクされます。 |
| N'Waitfor'       | 制限されているときに遅延することがなく、コマンドはすぐに返します。 |
  
## <a name="permissions"></a>アクセス許可

実行中のプリンシパルが必要、`CONTROL`データベースに対する権限。
  
## <a name="see-also"></a>参照

 [機能の制限](../../relational-databases/security/feature-restrictions.md)