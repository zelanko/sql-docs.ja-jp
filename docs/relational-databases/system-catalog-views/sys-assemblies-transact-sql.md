---
title: "sys.assemblies (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.assemblies
- assemblies_TSQL
- sys.assemblies_TSQL
- assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assemblies catalog view
ms.assetid: e321753f-293f-42ab-b225-d118713df40b
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6e539377bf1c0d7c4060238baf26a152f02dbbdd
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysassemblies-transact-sql"></a>sys.assemblies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  アセンブリごとに 1 行のデータを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|アセンブリの名前。 データベース内で一意です。|  
|**principal_id**|**int**|このアセンブリを所有するプリンシパルの ID。|  
|**assembly_id**|**int**|アセンブリ識別番号。 データベース内で一意です。|  
|**clr_name**|**nvarchar (4000)**|アセンブリの簡単な名前、バージョン番号、カルチャ、公開キー、およびアーキテクチャをエンコードする正規文字列。 この値は、共通言語ランタイム (CLR) 側でアセンブリを一意に識別する値です。|  
|**permission_set**|**tinyint**|アセンブリに対する権限セットまたはセキュリティ レベル。<br /><br /> 1 = 安全なアクセス<br /><br /> 2 = 外部アクセス<br /><br /> 3 = 安全でないアクセス|  
|**permission_set_desc**|**nvarchar(60)**|アセンブリに対する権限セットまたはセキュリティ レベルの説明。<br /><br /> SAFE_ACCESS<br /><br /> EXTERNAL_ACCESS<br /><br /> UNSAFE_ACCESS|  
|**is_visible**|**bit**|1 = アセンブリは [!INCLUDE[tsql](../../includes/tsql-md.md)] エントリ ポイントを登録するため表示されます。<br /><br /> 0 = アセンブリは管理されている呼び出し元のみを対象にしています。 つまりアセンブリは、データベース内の他のアセンブリに対して内部実装を提供します。|  
|**create_date**|**datetime**|アセンブリが作成または登録された日付。|  
|**modify_date**|**datetime**|アセンブリが変更された日付。|  
|**is_user_defined**|**bit**|アセンブリのソースを示します。<br /><br /> 0 = システム定義のアセンブリ (に対する Microsoft.SqlServer.Types など、 **hierarchyid**データ型)<br /><br /> 1 = ユーザー定義のアセンブリ|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR アセンブリ カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ASSEMBLYPROPERTY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/assemblyproperty-transact-sql.md)  
  
  
