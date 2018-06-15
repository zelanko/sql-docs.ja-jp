---
title: sp_db_selective_xml_index (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_db_selective_xml_index_TSQL
- sp_db_selective_xml_index
dev_langs:
- TSQL
helpviewer_keywords:
- sp_db_selective_xml_index procedure
ms.assetid: 017301a2-4a23-4e68-82af-134f3d4892b3
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: af5f2cd7f027c583c8eeb262834ce90700b37ae0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33237039"
---
# <a name="spdbselectivexmlindex-transact-sql"></a>sp_db_selective_xml_index (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに対して選択的 XML インデックス機能を有効または無効にします。 パラメーターを指定しないでストアド プロシージャを呼び出すと、選択的 XML インデックスが特定のデータベースで有効になっている場合は 1 が返されます。  
  
> [!NOTE]  
>  このストアド プロシージャを使用して、選択的 XML インデックスを無効にするために、データベース必要がありますに配置する、単純復旧モードを使用して、 [ALTER DATABASE SET Options &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md)コマンド。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
  
      sys.sp_db_selective_xml_index[[ @db_name = ] 'db_name'],   
[[ @action = ] 'action']  
```  
  
## <a name="arguments"></a>引数  
 **[db_name @ =]** **'***db_name***'**  
 選択的 XML インデックスを有効または無効にするデータベースの名前。 場合*db_name* NULL の場合は、現在のデータベースが使用されます。  
  
 [  **@action =** ] **'***アクション***'**  
 インデックスを有効にするか無効にするかを決定します。 on、true、off、または false 以外の別の値を渡すと、エラーが発生します。  
  
```  
  
Allowed values: 'on', 'off', 'true', 'false'  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 **1**選択的 XML インデックスが特定のデータベースで有効になっている場合。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-enable-selective-xml-index-functionality"></a>A. 選択的 XML インデックス機能を有効にする  
 次の例では、現在のデータベースに対して選択的 XML インデックスを有効にします。  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = NULL  
  , @action = N'on';  
GO  
```  
  
 次の例では、AdventureWorks2012 データベースに対して選択的 XML インデックスを有効にします。  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = N'AdventureWorks2012'  
  , @action = N'true';  
GO  
```  
  
### <a name="b-disable-selective-xml-index-functionality"></a>B. 選択的 XML インデックス機能を無効にする  
 次の例では、現在のデータベースに対して選択的 XML インデックスを無効にします。  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = NULL  
  , @action = N'off';  
GO  
```  
  
 次の例では、AdventureWorks2012 データベースに対して選択的 XML インデックスを無効にします。  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = N'AdventureWorks2012'  
  , @action = N'false';  
GO  
```  
  
### <a name="c-detect-if-selective-xml-index-is-enabled"></a>C. 選択的 XML インデックスが有効かどうかを検出する  
 次の例では、選択的 XML インデックスが有効かどうかを検出します。 選択的 XML インデックスが有効な場合は、1 が返されます。  
  
```  
EXECUTE sys.sp_db_selective_xml_index;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [選択的 XML インデックス &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)  
  
  
