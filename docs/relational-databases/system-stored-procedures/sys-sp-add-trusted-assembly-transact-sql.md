---
title: "sys.sp_add_trusted_assembly (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_add_trusted_assembly_TSQL
- sp_add_trusted_assembly
- sys.sp_add_trusted_assembly_TSQL
- sys.sp_add_trusted_assembly
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_add_trusted_assembly
ms.assetid: 
caps.latest.revision: 
author: tmullaney
ms.author: thmullan
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b634a990abcd9f763c851eaf1fbdde4d022ca25e
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="sysspaddtrustedassembly-transact-sql"></a>sys.sp_add_trusted_assembly (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

サーバーの信頼されたアセンブリの一覧にアセンブリを追加します。

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


## <a name="syntax"></a>構文
```  
sp_add_trusted_assembly 
    [ @hash = ] 'value'
    [ , [ @description = ] 'description' ]
```  

## <a name="remarks"></a>解説  

この手順で追加するアセンブリ[sys.trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md)です。

## <a name="arguments"></a>引数

[ @hash =] '*値*'  
サーバーの信頼されたアセンブリの一覧に追加するアセンブリの SHA2_512 ハッシュ値。 信頼されたアセンブリを読み込むときに可能性があります[CLR 厳格なセキュリティ](../../database-engine/configure-windows/clr-strict-security.md)が有効なアセンブリが署名されていないか、データベースを信頼可能としてマークされていない場合でもです。

[ @description =] '*説明*'  
省略可能なユーザー定義アセンブリの説明。 簡易名、バージョン番号、カルチャ、公開キー、および信頼するアセンブリのアーキテクチャをエンコードする正規名を使用することをお勧めします。 この値は一意に共通言語ランタイム (CLR) 側にアセンブリを識別、sys.assemblies で clr_name 値と同じです。 

## <a name="permissions"></a>権限

メンバーシップが必要、`sysadmin`固定サーバー ロールまたは`CONTROL SERVER`権限です。

## <a name="examples"></a>使用例  

次の例では、という名前のアセンブリ`pointudt`サーバーの信頼されたアセンブリの一覧にします。 これらの値がから利用可能な[sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)です。     

```  
EXEC sp_add_trusted_assembly 0x8893AD6D78D14EE43DF482E2EAD44123E3A0B684A8873C3F7BF3B5E8D8F09503F3E62370CE742BBC96FE3394477214B84C7C1B0F7A04DCC788FA99C2C09DFCCC, 
N'pointudt, version=0.0.0.0, culture=neutral, publickeytoken=null, processorarchitecture=msil';
```  

## <a name="see-also"></a>参照  
  [sys.sp_drop_trusted_assembly](sys-sp-drop-trusted-assembly-transact-sql.md)  
  [sys.trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md)  
  [アセンブリ &#40; です。Transact SQL と &#41; です。](../../t-sql/statements/create-assembly-transact-sql.md)  
  [CLR の厳格なセキュリティ](../../database-engine/configure-windows/clr-strict-security.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  

