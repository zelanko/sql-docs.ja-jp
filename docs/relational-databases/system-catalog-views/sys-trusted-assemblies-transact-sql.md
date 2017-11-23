---
title: "sys.trusted_assemblies (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- trusted_assemblies_TSQL
- trusted_assemblies
- sys.trusted_assemblies_TSQL
- sys.trusted_assemblies
dev_langs: TSQL
helpviewer_keywords: sys.trusted_assemblies
ms.assetid: 
caps.latest.revision: 
author: tmullaney
ms.author: thmullan;rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2ef97b33df620457102d79ad9535a3550014aa55
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="systrustedassemblies-transact-sql"></a>sys.trusted_assemblies (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

サーバーの信頼されたアセンブリごとに、行を格納します。

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


|列名 |データ型 |Description |
|--- |--- |--- |
|ハッシュ |varbinary (8000) |SHA2_512 コンテンツのハッシュのアセンブリ。 |
|description |nvarchar (4000) |省略可能なユーザー定義アセンブリの説明。 簡易名、バージョン番号、カルチャ、公開キー、および信頼するアセンブリのアーキテクチャをエンコードする正規名を使用することをお勧めします。 この値は一意に共通言語ランタイム (CLR) 側にアセンブリを識別、sys.assemblies で clr_name 値と同じです。 |
|create_date |datetime2 |アセンブリが信頼されているアセンブリの一覧に追加された日付。 |
|created_by |nvarchar (128) |アセンブリが一覧に追加したプリンシパルのログイン名。 |
| | | |


## <a name="remarks"></a>解説  

使用して**sp_add_trusted_assembly を追加する必要があります**と**sys.trusted_assemblies を追加する必要があります**追加または削除するアセンブリから`sys.trusted_assemblies`です。

## <a name="see-also"></a>参照  
  [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md) [sys.sp_drop_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) [DROP ASSEMBLY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-assembly-transact-sql.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  

