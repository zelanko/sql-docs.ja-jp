---
title: "sys.endpoint_webmethods (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.endpoint_webmethods_TSQL
- sys.endpoint_webmethods
- endpoint_webmethods_TSQL
- sys.http_soap_methods_TSQL
- endpoint_webmethods
- sys.http_soap_methods
dev_langs:
- TSQL
helpviewer_keywords:
- sys.endpoint_webmethods catalog view
ms.assetid: 7dad0cf6-eafa-47cf-98cc-75ba8d3c7959
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 93053b36893b6812128d2bb397a656d395f839af
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sysendpointwebmethods-transact-sql"></a>sys.endpoint_webmethods (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 SOAP 対応 HTTP エンドポイントに定義されている行 FOR EACH SOAP メソッドを保持します。 Endpoint_id と名前空間列の組み合わせは一意です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|endpoint_id|**int**|Web メソッドが定義されているエンドポイントの ID です。|  
|namespace|**nvarchar (384)**|Web メソッドの名前空間です。|  
|method_alias|**nvarchar(64)**|メソッドの別名です。<br /><br /> 注:[!INCLUDE[tsql](../../includes/tsql-md.md)]識別子は、WSDL メソッド名では無効な文字を許可します。<br /><br /> エイリアスを使用すると、基になる実際のエンドポイントの WSDL 記述に公開されている名前[!INCLUDE[tsql](../../includes/tsql-md.md)]web メソッドが呼び出されるときに呼び出される実行可能オブジェクト。|  
|object_name|**nvarchar (776)**|NAME = オプションで指定された、Web メソッドのリダイレクト先のオブジェクト名です。 名前の部分がピリオド (.) で区切られ、角かっこを使用して区切られた`[``]`です。<br /><br /> オブジェクト名は WSDL オプションで指定されている、3 つの部分から成る名前でなければなりません。|  
|result_schema|**tinyint**|XSD (ある場合) を応答と共に返送するかどうかを指定するオプションです。<br /><br /> 0 = なし<br /><br /> 1 = 標準<br /><br /> 2 = 既定|  
|result_schema_desc|**nvarchar (60)**|XSD (ある場合) を応答と共に返送するかどうかを指定するオプションの説明です。<br /><br /> なし<br /><br /> STANDARD<br /><br /> DEFAULT|  
|result_format|**tinyint**|応答において結果をどのようにフォーマットするかを指定するオプションです。<br /><br /> 1 = ALL_RESULTS<br /><br /> 2 = ROWSETS_ONLY<br /><br /> 3 = なし|  
|result_format_desc|**nvarchar (60)**|応答において結果をどのようにフォーマットするかを指定するオプションの説明です。<br /><br /> ALL_RESULTS<br /><br /> ROWSETS_ONLY<br /><br /> なし|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [エンドポイントのカタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
