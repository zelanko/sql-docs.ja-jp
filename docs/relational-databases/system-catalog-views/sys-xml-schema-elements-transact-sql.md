---
title: "sys.xml_schema_elements (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sys.xml_schema_elements
- sys.xml_schema_elements_TSQL
- xml_schema_elements
- xml_schema_elements_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_elements catalog view
ms.assetid: 190ed0cd-0c5e-4607-9db4-9e77cacf17d7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e4d329881c8e895b7f2f1a3b06080b869218a93e
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysxmlschemaelements-transact-sql"></a>sys.xml_schema_elements (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XML スキーマ コンポーネントは、型ごとに 1 行を返します**symbol_space**の**E**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<継承された列 >**|**--**|列を継承[sys.xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md)です。|  
|**is_default_fixed**|**bit**|1 = 既定値は、固定値。 この値は XML インスタンス内で無効にできません。<br /><br /> 0 = デフォルト値は要素の固定値ではありません  (既定)。|  
|**is_abstract**|**bit**|1 = 要素は abstract であり、インスタンス ドキュメント内では使用できません。 要素の代替グループのメンバーは、インスタンス ドキュメント内に表示される必要があります。<br /><br /> 0 = 要素は abstract ではありません  (既定)。|  
|**is_nillable**|**bit**|1 = 要素は nillable です。<br /><br /> 0 = 要素は nillable ではありません  (既定値)。|  
|**must_be_qualified**|**bit**|1 = 要素には明示的に名前空間の修飾名を追加する必要があります。<br /><br /> 0 = 要素には暗黙的に名前空間の修飾名が追加されます  (既定値)。|  
|**is_extension_blocked**|**bit**|1 = 拡張型のインスタンスへの置換はブロックされます。<br /><br /> 0 = 拡張型への置換は許可されます  (既定値)。|  
|**is_restriction_blocked**|**bit**|1 = 制限型のインスタンスへの置換はブロックされます。<br /><br /> 0 = 制限型への置換は許可されます  (既定値)。|  
|**is_substitution_blocked**|**bit**|1 = 代替グループのインスタンスは使用できません。<br /><br /> 0 = 代替グループへの置換は許可されます  (既定値)。|  
|**is_final_extension**|**bit**|1 = 拡張型のインスタンスへの置換は許可されません。<br /><br /> 0 = 拡張型のインスタンスへの置換は許可されます  (既定値)。|  
|**is_final_restriction**|**bit**|1 = 制限型のインスタンスへの置換は許可されません。<br /><br /> 0 = 制限型のインスタンスへの置換は許可されます  (既定値)。|  
|**default_value**|**nvarchar (4000)**|要素の既定値。 既定値が指定されていない場合は NULL です。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML スキーマと #40 です。XML 型システム &#41;カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
