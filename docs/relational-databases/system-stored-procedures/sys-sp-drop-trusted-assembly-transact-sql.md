---
title: sys.sp_drop_trusted_assembly (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_drop_trusted_assembly_TSQL
- sp_drop_trusted_assembly
- sys.sp_drop_trusted_assembly_TSQL
- sys.sp_drop_trusted_assembly
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_drop_trusted_assembly
ms.assetid: ''
caps.latest.revision: ''
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 2ffdc0c87a798b23ce25e544b26ea63132495b53
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysspdroptrustedassembly-transact-sql"></a>sys.sp_drop_trusted_assembly (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

サーバー上の信頼されたアセンブリの一覧からアセンブリを削除します。

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


## <a name="syntax"></a>構文
```  
sp_drop_trusted_assembly 
    [ @hash = ] 'value'
```  

## <a name="arguments"></a>引数

[ @hash =] '*値*'  
サーバーの信頼されたアセンブリの一覧から削除するアセンブリの SHA2_512 ハッシュ値。 アセンブリが署名されていないか、データベースを信頼可能としてマークされていない場合でも、clr の厳格なセキュリティが有効にすると、信頼されたアセンブリを読み込むことがあります。

## <a name="remarks"></a>解説  

この手順からアセンブリを削除する[sys.trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md)です。

## <a name="permissions"></a>権限

メンバーシップが必要、`sysadmin`固定サーバー ロールまたは`CONTROL SERVER`権限です。

## <a name="examples"></a>使用例  

次の例では、サーバーの信頼されたアセンブリの一覧からアセンブリ ハッシュを削除します。  

```  
EXEC sp_drop_trusted_assembly 
0x8893AD6D78D14EE43DF482E2EAD44123E3A0B684A8873C3F7BF3B5E8D8F09503F3E62370CE742BBC96FE3394477214B84C7C1B0F7A04DCC788FA99C2C09DFCCC; 
```  

## <a name="see-also"></a>参照  
  [sys.sp_add_trusted_assembly](sys-sp-add-trusted-assembly-transact-sql.md) [sys.trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md) [DROP ASSEMBLY &#40;TRANSACT-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  

