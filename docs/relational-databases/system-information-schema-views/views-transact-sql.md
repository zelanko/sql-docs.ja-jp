---
title: VIEWS (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- VIEWS_TSQL
- VIEWS
dev_langs:
- TSQL
helpviewer_keywords:
- VIEWS view
- INFORMATION_SCHEMA.VIEWS view
ms.assetid: 6119bc94-0b22-45d4-a34b-967afd810a9d
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b4e2a969450c2ec4593c7daec1b9c9b203b18410
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078365"
---
# <a name="views-transact-sql"></a>ビュー (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースで現在のユーザーがアクセスできるビューを表す 1 行のデータを返します。  
  
 これらのビューから情報を取得するには、INFORMATION_SCHEMA の完全修飾名を指定し**ます。**_view_name_。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|ビュー修飾子。|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|ビューを含むスキーマの名前です。<br /><br /> **&#42;&#42; の重要な &#42;&#42;** オブジェクトのスキーマを決定するために INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**TABLE_NAME**|**nvarchar (** 128 **)**|ビュー名。|  
|**VIEW_DEFINITION**|**nvarchar (** 4000 **)**|定義の長さが**nvarchar (** 4000 **)** よりも大きい場合、この列は NULL になります。 それ以外の場合は、ビュー定義のテキストです。|  
|**CHECK_OPTION**|**varchar (** 7 **)**|WITH CHECK OPTION の型。 元のビューが WITH CHECK OPTION を使用して作成されている場合、CASCADE です。 それ以外の場合は、NONE が返されます。|  
|**IS_UPDATABLE**|**varchar (** 2 **)**|ビューが更新可能かどうかを指定します。 常に NO が返されます。|  
  
## <a name="see-also"></a>参照  
 [システムビュー &#40;Transact-sql&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマビュー &#40;Transact-sql&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sql_modules &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [&#40;Transact-sql&#41;の表示](../../relational-databases/system-catalog-views/sys-views-transact-sql.md)  
  
  
