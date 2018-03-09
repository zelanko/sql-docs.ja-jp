---
title: "sys.system_parameters (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.system_parameters
- sys.system_parameters_TSQL
- system_parameters_TSQL
- system_parameters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_parameters catalog view
ms.assetid: 0d135c5f-68b5-4009-a0da-35e6abfee0ff
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a3cbff5c8c67b09f97ae8b1261aa5ab72b2981f7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syssystemparameters-transact-sql"></a>sys.system_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  パラメーターを持つシステム オブジェクトごとに 1 行のデータを格納します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|パラメーターが属しているオブジェクトの ID。|  
|**name**|**sysname**|パラメーターの名前です。 オブジェクト内で一意です。<br /><br /> オブジェクトがスカラー関数の場合、パラメーター名は、戻り値を表す行の空の文字列になります。|  
|**parameter_id**|**int**|パラメーターの ID です。 オブジェクト内で一意です。 場合は、オブジェクトがスカラー関数、 **parameter_id**戻り値 0 を = です。|  
|**system_type_id**|**tinyint**|パラメーターのシステム型の ID です。|  
|**user_type_id**|**int**|ユーザーが定義されているパラメーターの型の ID。<br /><br /> 型の名前を返すに参加させる、 [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)カタログをこの列に表示します。|  
|**max_length**|**smallint**|パラメーターの最大長 (バイト単位)。 値の-1 になりますが、列のデータ型の場合**varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、または**xml**です。|  
|**有効桁数**|**tinyint**|数値ベースの場合は、パラメーターの有効桁数です。それ以外の場合は、0 です。|  
|**小数点以下桁数**|**tinyint**|数値ベースの場合は、パラメーターの小数点以下桁数です。それ以外の場合は、0 です。|  
|**is_output**|**bit**|1 = パラメーターが出力 (またはを返す)。それ以外の場合、0 を返します。|  
|**is_cursor_ref**|**bit**|1 = パラメーターはカーソル参照パラメーターです。|  
|**has_default_value**|**bit**|1 = パラメーターに既定値です。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のみです。 このカタログ ビュー内の CLR オブジェクトの既定値が保持されます。したがって、この列には 0 に設定する値が常に[!INCLUDE[tsql](../../includes/tsql-md.md)]オブジェクト。 内のパラメーターの既定値を表示する、[!INCLUDE[tsql](../../includes/tsql-md.md)]オブジェクト、クエリ、**定義**の列、 [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)カタログ ビュー、またはを使用して、 [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md)システム関数です。|  
|**is_xml_document**|**bit**|1 = 内容が完全な XML ドキュメントです。<br /><br /> 0 = 内容がドキュメントの一部か、列のデータ型が**xml**です。|  
|**default_value です。**|**sql_variant**|場合**has_default_value** 1 の場合は、この列の値が、パラメーターの既定の値。 それ以外の場合は NULL です。|  
|**xml_collection_id**|**int**|パラメーターのデータ型が場合は 0 以外**xml** XML が型指定されたとします。 この値は、パラメーターの評価 XML スキーマ名前空間に含まれるコレクションの ID です。<br /><br /> 0 = XML スキーマ コレクションはありません。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)   
 [sys.all_parameters &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-all-parameters-transact-sql.md)  
  
  
