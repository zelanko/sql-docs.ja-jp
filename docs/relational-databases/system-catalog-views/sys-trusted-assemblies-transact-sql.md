---
title: trusted_assemblies (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql
ms.technology: system-objects
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
author: VanMSFT
ms.author: vanto
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c8144e6a134edf3331b34f5c91f6d676e6a9302f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733405"
---
# <a name="systrusted_assemblies-transact-sql"></a>sys.trusted_assemblies (Transact-SQL)  
[!INCLUDE[SQL Server 2017](../../includes/applies-to-version/sqlserver2017.md)]

サーバーの信頼されたアセンブリごとに1行の値を格納します。

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


|列名 |データ型 |説明 |
|--- |--- |--- |
|hash |varbinary(8000) |アセンブリコンテンツの SHA2_512 ハッシュ。 |
|description |nvarchar(4000) |アセンブリに関するオプションのユーザー定義の説明。 信頼するアセンブリの簡易名、バージョン番号、カルチャ、公開キー、およびアーキテクチャをエンコードする正規名を使用することをお勧めします。 この値は、共通言語ランタイム (CLR) 側でアセンブリを一意に識別するものであり、sys. アセンブリの clr_name 値と同じです。 |
|create_date |datetime2 |アセンブリが信頼されたアセンブリの一覧に追加された日付。 |
|created_by |nvarchar(128) |アセンブリをリストに追加したプリンシパルのログイン名。 |
| | | |


## <a name="remarks"></a>Remarks  

を使用して**sp_add_trusted_assembly を追加**し、 **sys を追加する必要**があります。また、からアセンブリを追加または削除 trusted_assemblies。 `sys.trusted_assemblies`

## <a name="see-also"></a>関連項目  
  [sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md) [sys. sp_drop_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) [drop assembly &#40;transact-sql&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  

