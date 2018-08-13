---
title: sys.sp_add_trusted_assembly (TRANSACT-SQL) |マイクロソフトのドキュメント
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
- sp_add_trusted_assembly_TSQL
- sp_add_trusted_assembly
- sys.sp_add_trusted_assembly_TSQL
- sys.sp_add_trusted_assembly
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_add_trusted_assembly
ms.assetid: ''
caps.latest.revision: ''
author: tmullaney
ms.author: thmullan
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: f2749313495c8aa76fb45cd9d9dfe8d5fc0bc90e
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39548434"
---
# <a name="sysspaddtrustedassembly-transact-sql"></a>sys.sp_add_trusted_assembly (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

サーバーの信頼されたアセンブリの一覧には、アセンブリを追加します。

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


## <a name="syntax"></a>構文
```  
sp_add_trusted_assembly 
    [ @hash = ] 'value'
    [ , [ @description = ] 'description' ]
```  

## <a name="remarks"></a>コメント  

この手順で追加するアセンブリ[sys.trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md)します。

## <a name="arguments"></a>引数

[ @hash =] '*値*'  
サーバーの信頼されたアセンブリの一覧に追加するアセンブリの SHA2_512 のハッシュ値。 アセンブリを読み込むことがあるときに信頼された[CLR strict security](../../database-engine/configure-windows/clr-strict-security.md)アセンブリが署名されていないか、データベースが信頼可能としてマークされていない場合でも有効です。

[ @description =] '*説明*'  
省略可能なユーザー定義アセンブリの説明。 簡易名、バージョン番号、カルチャ、公開キー、および信頼するアセンブリのアーキテクチャをエンコードする正規名を使用することをお勧めします。 この値は一意に共通言語ランタイム (CLR) 側でアセンブリを識別し、sys.assemblies clr_name 値と同じです。 

## <a name="permissions"></a>アクセス許可

メンバーシップが必要です、`sysadmin`固定サーバー ロールまたは`CONTROL SERVER`権限。

## <a name="examples"></a>使用例  

次の例では、という名前のアセンブリ`pointudt`サーバーの信頼されたアセンブリの一覧にします。 これらの値はから利用可能な[sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)します。     

```  
EXEC sp_add_trusted_assembly 0x8893AD6D78D14EE43DF482E2EAD44123E3A0B684A8873C3F7BF3B5E8D8F09503F3E62370CE742BBC96FE3394477214B84C7C1B0F7A04DCC788FA99C2C09DFCCC, 
N'pointudt, version=0.0.0.0, culture=neutral, publickeytoken=null, processorarchitecture=msil';
```  

## <a name="see-also"></a>参照  
  [sys.sp_drop_trusted_assembly](sys-sp-drop-trusted-assembly-transact-sql.md)  
  [sys.trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md)  
  [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)  
  [CLR の厳密なセキュリティ](../../database-engine/configure-windows/clr-strict-security.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  

