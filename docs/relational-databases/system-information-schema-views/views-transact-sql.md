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
ms.openlocfilehash: a24df8a9c4c85e94259f663b8319d1145a15b565
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83670302"
---
# <a name="views-transact-sql"></a>ビュー (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースで現在のユーザーがアクセスできるビューを表す 1 行のデータを返します。  
  
 これらのビューから情報を取得するには、INFORMATION_SCHEMA の完全修飾名を指定し**ます。**_view_name_。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|ビュー修飾子。|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|ビューを含むスキーマの名前です。<br /><br /> **&#42;&#42; 重要な**のは、オブジェクトのスキーマを検索する信頼できる方法は、 &#42;&#42;カタログビューに対してクエリを実行することだけです。|  
|**TABLE_NAME**|**nvarchar (** 128 **)**|ビューの名前。|  
|**VIEW_DEFINITION**|**nvarchar (** 4000 **)**|定義の長さが**nvarchar (** 4000 **)** よりも大きい場合、この列は NULL になります。 それ以外の場合は、ビュー定義のテキストです。|  
|**CHECK_OPTION**|**varchar (** 7 **)**|WITH CHECK OPTION の型。 元のビューが WITH CHECK OPTION を使用して作成されている場合、CASCADE です。 その他の場合は NONE が返されます。|  
|**IS_UPDATABLE**|**varchar (** 2 **)**|ビューが更新可能であるかどうかを指定します。 常に NO が返されます。|  
  
## <a name="see-also"></a>参照  
 [システムビュー &#40;Transact-sql&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマビュー &#40;Transact-sql&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.views &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-views-transact-sql.md)  
  
  
