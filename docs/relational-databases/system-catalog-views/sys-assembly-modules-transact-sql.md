---
title: sys.assembly_modules (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.assembly_modules
- sys.assembly_modules_TSQL
- assembly_modules
- assembly_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assembly_modules catalog view
ms.assetid: 5f9e644e-8065-49a2-b53d-db7df98f70d8
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d457f00cdab5d8b7e6584c895c9a9070a1d9e395
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysassemblymodules-transact-sql"></a>sys.assembly_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  共通言語ランタイム (CLR) アセンブリによって定義されている関数、プロシージャ、またはトリガーごとに 1 行のデータを返します。 このカタログ ビューは、CLR ストアド プロシージャ、CLR トリガー、または CLR 関数を、基になる実装にマップします。 種類が TA、AF、PC、FS、および FT のオブジェクトには、関連するアセンブリ モジュールがあります。 オブジェクトとアセンブリの間の関連を見つけるには、このカタログ ビューを他のカタログ ビューに結合します。 たとえば、CLR ストアド プロシージャを作成するときで表される 1 つの行**sys.objects**,、1 つの行**sys.procedures** (から継承される**sys.objects**)、および1 つの行**sys.assembly_modules**です。 ストアド プロシージャ自体は内のメタデータで表される**sys.objects**と**sys.procedures**です。 プロシージャの基になる CLR 実装への参照は**sys.assembly_modules**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|SQL オブジェクトのオブジェクト ID 番号。 データベース内で一意です。|  
|**assembly_id**|**int**|モジュールが作成された元のアセンブリの ID。|  
|**assembly_class**|**sysname**|このモジュールを定義しているアセンブリ内のクラスの名前です。|  
|**assembly_method**|**sysname**|内のメソッドの名前、 **assembly_class**このモジュールを定義します。<br /><br /> 集計関数 (AF) の場合は NULL です。|  
|**null_on_null_input**|**bit**|モジュールは、任意の NULL 入力に対して NULL 出力を生成するように宣言されています。|  
|**execute_as_principal_id**|**int**|CLR 関数、ストアド プロシージャ、またはトリガーの EXECUTE AS 句によって指定されている、コンテキストの実行が行われるデータベース プリンシパルの ID です。<br /><br /> NULL = EXECUTE AS CALLER。 これは既定値です。<br /><br /> 指定したデータベース プリンシパルの ID = EXECUTE AS SELF、EXECUTE AS *user_name*、または EXECUTE AS *login_name*です。<br /><br /> -2 = EXECUTE AS OWNER。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
