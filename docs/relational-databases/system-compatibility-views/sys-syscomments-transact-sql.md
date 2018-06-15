---
title: sys.syscomments (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 53
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1020b8b980522d0c7dc6f82204e95128dd270cc6
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33221531"
---
# <a name="syssyscomments-transact-sql"></a>sys.syscomments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース内のビュー、ルール、既定値、トリガー、CHECK 制約、DEFAULT 制約、およびストアド プロシージャごとに 1 つのエントリを保持します。 **テキスト**列には、元の SQL 定義ステートメントが含まれています。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに sys.sql モジュールを使用することをお勧めします。 詳細については、次を参照してください。 [sys.sql_modules &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|このテキストが適用されるオブジェクトの ID です。|  
|**number**|**smallint**|プロシージャがグループ化されている場合は、グループ内の番号です。<br /><br /> 0 = エントリはプロシージャではない|  
|**colid**|**smallint**|オブジェクトの定義が 4,000 文字を超える場合の行のシーケンス番号です。|  
|**ステータス**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**ctext**|**varbinary(8000)**|SQL 定義ステートメントの生のバイトです。|  
|**texttype**|**smallint**|0 = ユーザーが指定するパラメーター<br /><br /> 1 = システムが指定するパラメーター<br /><br /> 4 = 暗号化コメント|  
|**言語**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**encrypted**|**bit**|プロシージャ定義が暗号化されているかどうかを示します。<br /><br /> 0 = 暗号化されていない<br /><br /> 1 = 暗号化されている<br /><br /> **\*\* 重要な\* \*** ストアド プロシージャの定義を難読化するには、暗号化のキーワードを含む CREATE PROCEDURE を使用します。|  
|**圧縮**|**bit**|常に 0 を返します。 これは、プロシージャが圧縮されていることを示します。|  
|**text**|**nvarchar (4000)**|SQL 定義ステートメントの実際のテキストです。<br /><br /> デコードされた式のセマンティクスは元のテキストと同じですが、構文も同じであるとは限りません。 たとえば、デコードされた式からは空白文字が削除されます。<br /><br /> これは、 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-互換のビューを現在の情報を取得する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]構造しより多くの文字を返すことができます、 **nvarchar (4000)** 定義します。 **sp_help**返します**nvarchar (4000)** テキスト列のデータ型として。 使用するときに**syscomments**使用を検討して**nvarchar (max)** です。 新しい開発作業では使用しないで**syscomments**です。|  
  
## <a name="see-also"></a>参照  
 [システム ビューへのシステム テーブルのマッピング&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
