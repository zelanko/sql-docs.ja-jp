---
title: システム情報スキーマ ビュー (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-information-schema-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- information schema views
- schemas [SQL Server], information schema views
- metadata [SQL Server], views
- views [SQL Server], information schema
- system views [SQL Server], information schema
ms.assetid: 7e9f1dfe-27e9-40e7-8fc7-bfc5cae6be10
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 142d997b85caf9dd84b4b1da742a53286f672c94
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="system-information-schema-views-transact-sql"></a>システム情報スキーマ ビュー (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  情報スキーマ ビューは、いくつかの方法のいずれかの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータの取得を提供します。 情報スキーマ ビューでは、システム テーブルに依存しない、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メタデータの内部ビューが提供されます。 基になるシステム テーブルに大きな変更が加えられても、情報スキーマ ビューによって、アプリケーションは正しく動作できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に含まれる情報スキーマ ビューは、ISO 標準定義の INFORMATION_SCHEMA に従います。  
  
> [!IMPORTANT]  
>  情報スキーマ ビューに対しては、旧バージョンとの互換性を維持できない変更がいくつか加えられています。 これらの変更は、個々のビューのトピックで説明します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 現在のサーバーを参照するときは、3 部構成の名前付け規則をサポートしています。 ISO 標準も、3 つの要素で構成される名前付け規則をサポートします。 しかし、両方の名前付け規則で使用される名前は同じではありません。 情報スキーマ ビューは、INFORMATION_SCHEMA という特殊スキーマで定義されます。 このスキーマは、各データベースに含まれます。 各情報スキーマ ビューは、特定のデータベースに格納されているすべてのデータ オブジェクトのメタデータで構成されています。 次の表は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 名と SQL 標準名の関係を示しています。  
  
|SQL Server 名|対応する等価な SQL 標準名|  
|---------------------|-----------------------------------------------|  
|データベース|Catalog|  
|スキーマ|スキーマ|  
|オブジェクト|オブジェクト|  
|ユーザー定義データ型|[ドメイン]|  
  
 この名前マッピング規則は、次の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の ISO 互換ビューに適用されます。  
  
|||  
|-|-|  
|[CHECK_CONSTRAINTS](../../relational-databases/system-information-schema-views/check-constraints-transact-sql.md)|[REFERENTIAL_CONSTRAINTS](../../relational-databases/system-information-schema-views/referential-constraints-transact-sql.md)|  
|[COLUMN_DOMAIN_USAGE](../../relational-databases/system-information-schema-views/column-domain-usage-transact-sql.md)|[ROUTINES](../../relational-databases/system-information-schema-views/routines-transact-sql.md)|  
|[COLUMN_PRIVILEGES](../../relational-databases/system-information-schema-views/column-privileges-transact-sql.md)|[ROUTINE_COLUMNS](../../relational-databases/system-information-schema-views/routine-columns-transact-sql.md)|  
|[COLUMNS](../../relational-databases/system-information-schema-views/columns-transact-sql.md)|[SCHEMATA](../../relational-databases/system-information-schema-views/schemata-transact-sql.md)|  
|[CONSTRAINT_COLUMN_USAGE](../../relational-databases/system-information-schema-views/constraint-column-usage-transact-sql.md)|[TABLE_CONSTRAINTS](../../relational-databases/system-information-schema-views/table-constraints-transact-sql.md)|  
|[CONSTRAINT_TABLE_USAGE](../../relational-databases/system-information-schema-views/constraint-table-usage-transact-sql.md)|[TABLE_PRIVILEGES](../../relational-databases/system-information-schema-views/table-privileges-transact-sql.md)|  
|[DOMAIN_CONSTRAINTS](../../relational-databases/system-information-schema-views/domain-constraints-transact-sql.md)|[TABLES](../../relational-databases/system-information-schema-views/tables-transact-sql.md)|  
|[DOMAINS](../../relational-databases/system-information-schema-views/domains-transact-sql.md)|[VIEW_COLUMN_USAGE](../../relational-databases/system-information-schema-views/view-column-usage-transact-sql.md)|  
|[KEY_COLUMN_USAGE](../../relational-databases/system-information-schema-views/key-column-usage-transact-sql.md)|[VIEW_TABLE_USAGE](../../relational-databases/system-information-schema-views/view-table-usage-transact-sql.md)|  
|[PARAMETERS](../../relational-databases/system-information-schema-views/parameters-transact-sql.md)|[VIEWS](../../relational-databases/system-information-schema-views/views-transact-sql.md)|  
  
 また、いくつかのビューは、文字データやバイナリ データなど、別のクラスのデータへの参照を含んでいます。  
  
 情報スキーマ ビューを参照する場合は、`INFORMATION_SCHEMA` スキーマ名を含む修飾名を使用する必要があります。 以下に例を示します。  
  
```  
SELECT TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME, COLUMN_DEFAULT  
FROM AdventureWorks2012.INFORMATION_SCHEMA.COLUMNS  
WHERE TABLE_NAME = N'Product';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
