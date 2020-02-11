---
title: xml_schema_types (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_types_TSQL
- xml_schema_types_TSQL
- sys.xml_schema_types
- xml_schema_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_types catalog view
ms.assetid: 441ba49d-f778-4fa1-98c4-ced375a01a34
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0a78730509cc1f9eeec83b8d9ff9cb0917e0ed99
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68060434"
---
# <a name="sysxml_schema_types-transact-sql"></a>xml_schema_types (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **T**の**symbol_space**型である XML スキーマコンポーネントごとに1行の値を返します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**\<継承された列>**||[Xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md)から列を継承します。|  
|**is_abstract**|**bit**|1 = 型は抽象型です。 この型の要素のすべてのインスタンスは、抽象型ではない派生型を示すために、 **xsi: type**を使用する必要があります。<br /><br /> 0 = 型は abstract ではありません  (既定値)。|  
|**allows_mixed_content**|**bit**|1 = 混合コンテンツは許可されます。<br /><br /> 0 = 混合コンテンツは許可されていません。 (既定値)。|  
|**is_extension_blocked**|**bit**|1 = **complexType**定義の block 属性または先祖\<> スキーマの**blockdefault**属性が "extension" または "#all" に設定されている場合、型の拡張による置換はインスタンスでブロックされます。<br /><br /> 0 = 拡張による置き換えはブロックされません。|  
|**is_restriction_blocked**|**bit**|1 = **complexType**定義の block 属性、または先祖\<スキーマ> 要素情報項目の**blockdefault**属性が "restriction" または "#all" に設定されている場合、型の制限付きの置換はインスタンスでブロックされます。<br /><br /> 0 = 制約による置き換えはブロックされません  (既定値)。|  
|**is_final_extension**|**bit**|1 = **complexType**定義の final 属性、または先祖\<スキーマ> 要素情報項目の**finaldefault**属性が "extension" または "#all" に設定されている場合、型の拡張による派生はブロックされます。<br /><br /> 0 = 拡張は許可されます  (既定値)。|  
|**is_final_restriction**|**bit**|1 = simple または**complexType**定義の final 属性、または先祖\<スキーマ> 要素情報項目の**finaldefault**属性が "restriction" または "#all" に設定されている場合、型の制約による派生はブロックされます。<br /><br /> 0 = 制約は許可されます  (既定値)。|  
|**is_final_list_member**|**bit**|1 = この単純型は、リスト項目の型として使用できません。<br /><br /> 0 = この型は複合型、またはリスト項目の型として使用できます  (既定値)。|  
|**is_final_union_member**|**bit**|1 = この単純型は、共用体型のメンバー型として使用することはできません。<br /><br /> 0 = この型は複合型です。 または、共用体メンバー型として使用することもできます。 (既定値)。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Xml スキーマ &#40;XML 型システム&#41; カタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
