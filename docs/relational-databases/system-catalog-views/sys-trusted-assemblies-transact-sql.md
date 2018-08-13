---
title: sys.trusted_assemblies (Transact SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- trusted_assemblies_TSQL
- trusted_assemblies
- sys.trusted_assemblies_TSQL
- sys.trusted_assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trusted_assemblies
ms.assetid: ''
caps.latest.revision: ''
author: tmullaney
ms.author: thmullan
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: a4b98f0bf099a0218d292220e83a81989855ad24
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39560152"
---
# <a name="systrustedassemblies-transact-sql"></a>sys.trusted_assemblies (Transact SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

サーバーの各信頼されたアセンブリの行が含まれています。

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


|列名 |データ型 |説明 |
|--- |--- |--- |
|ハッシュ |varbinary (8000) |アセンブリの内容のハッシュを SHA2_512。 |
|description |nvarchar (4000) |省略可能なユーザー定義アセンブリの説明。 簡易名、バージョン番号、カルチャ、公開キー、および信頼するアセンブリのアーキテクチャをエンコードする正規名を使用することをお勧めします。 この値は一意に、共通言語ランタイム (CLR) 側でアセンブリを識別する、sys.assemblies で clr_name の値と同じです。 |
|create_date |datetime2 |アセンブリが信頼されたアセンブリの一覧に追加された日付。 |
|created_by |nvarchar (128) |アセンブリが一覧に追加したプリンシパルのログイン名。 |
| | | |


## <a name="remarks"></a>コメント  

使用**sp_add_trusted_assembly を追加する必要があります**と**sys.trusted_assemblies を追加する必要があります**を追加または削除からのアセンブリの`sys.trusted_assemblies`です。

## <a name="see-also"></a>参照  
  [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md) [sys.sp_drop_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) [DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  

