---
title: sys. assemblies (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 19577afb746e3b005dffd803d86351d8a4b0eca4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001208"
---
# <a name="sysassemblies-transact-sql"></a>sys. アセンブリ (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  アセンブリごとに1行の値を返します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|アセンブリの名前。 データベース内で一意です。|  
|**principal_id**|**int**|このアセンブリを所有するプリンシパルの ID。|  
|**assembly_id**|**int**|アセンブリ識別番号。 データベース内で一意です。|  
|**clr_name**|**nvarchar(4000)**|アセンブリの簡単な名前、バージョン番号、カルチャ、公開キー、およびアーキテクチャをエンコードする正規文字列。 この値は、共通言語ランタイム (CLR) 側でアセンブリを一意に識別する値です。|  
|**permission_set**|**tinyint**|アセンブリの権限セット/セキュリティレベル。<br /><br /> 1 = 安全なアクセス<br /><br /> 2 = 外部アクセス<br /><br /> 3 = 安全でないアクセス|  
|**permission_set_desc**|**nvarchar (60)**|アセンブリに対する権限セットまたはセキュリティ レベルの説明。<br /><br /> SAFE_ACCESS<br /><br /> EXTERNAL_ACCESS<br /><br /> UNSAFE_ACCESS|  
|**is_visible**|**bit**|1 = アセンブリは [!INCLUDE[tsql](../../includes/tsql-md.md)] エントリ ポイントを登録するため表示されます。<br /><br /> 0 = アセンブリは管理されている呼び出し元のみを対象にしています。 つまり、アセンブリによって、データベース内の他のアセンブリの内部実装が提供されます。|  
|**create_date**|**DATETIME**|アセンブリが作成または登録された日付。|  
|**modify_date**|**DATETIME**|アセンブリが変更された日付。|  
|**is_user_defined**|**bit**|アセンブリのソースを示します。<br /><br /> 0 = システム定義のアセンブリ ( **hierarchyid**データ型の場合は、Microsoft. SqlServer. Types など)<br /><br /> 1 = ユーザー定義のアセンブリ|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR アセンブリカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ASSEMBLYPROPERTY &#40;Transact-sql&#41;](../../t-sql/functions/assemblyproperty-transact-sql.md)  
  
  
