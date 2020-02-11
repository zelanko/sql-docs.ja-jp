---
title: .sys (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.syscomments_TSQL
- syscomments
- syscomments_TSQL
- sys.syscomments
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syscomments compatibility view
- syscomments system table
ms.assetid: 767dd410-6bc9-4c4a-ab0f-6d2cf6163426
author: rothja
ms.author: jroth
ms.openlocfilehash: 183fa2fc1a674ec1cc987c265f5a0d4c399e27cc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68010748"
---
# <a name="syssyscomments-transact-sql"></a>.sys (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース内のビュー、ルール、既定値、トリガー、CHECK 制約、DEFAULT 制約、およびストアド プロシージャごとに 1 つのエントリを保持します。 **Text**列には、元の SQL 定義ステートメントが含まれています。  
  
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに sys.sql モジュールを使用することをお勧めします。 詳細については、「 [sys. sql_modules &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)」を参照してください。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**番号**|**int**|このテキストを適用するオブジェクト ID。|  
|**number**|**smallint**|グループ化されている場合は、プロシージャグループ内の数値。<br /><br /> 0 = エントリはプロシージャではありません。|  
|**colid**|**smallint**|4000文字を超えるオブジェクト定義の行シーケンス番号。|  
|**オンライン**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**ctext**|**varbinary (8000)**|SQL 定義ステートメントの生バイト。|  
|**texttype**|**smallint**|0 = ユーザーが指定したコメント<br /><br /> 1 = システムが指定するパラメーター<br /><br /> 4 = 暗号化されたコメント|  
|**言語**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**暗号**|**bit**|プロシージャ定義を難読化するかどうかを示します。<br /><br /> 0 = 暗号化されていない<br /><br /> 1 = 難読化<br /><br /> ** \*重要\* \* **ストアドプロシージャの定義を難読化するには、ENCRYPTION キーワードを使用して CREATE PROCEDURE を使用します。|  
|**た**|**bit**|常に 0 を返します。 これは、プロシージャが圧縮されていることを示します。|  
|**本文**|**nvarchar(4000)**|SQL 定義ステートメントの実際のテキストです。<br /><br /> デコードされた式のセマンティクスは元のテキストと同じです。ただし、構文上の保証はありません。 たとえば、空白文字は、デコードされた式から削除されます。<br /><br /> この[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]互換のビューは、現在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の構造から情報を取得し、 **nvarchar (4000)** 定義よりも多くの文字を返すことができます。 **sp_help**は、 **nvarchar (4000)** をテキスト列のデータ型として返します。 **Syscomments**を使用する場合は、 **nvarchar (max)** の使用を検討してください。 新しい開発作業では、 **syscomments**を使用しないでください。|  
  
## <a name="see-also"></a>参照  
 [システムビューへのシステムテーブルのマッピング &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-sql&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
