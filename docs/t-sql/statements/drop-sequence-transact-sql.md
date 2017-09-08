---
title: "ドロップ シーケンス (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SEQUENCE
- DROP_SEQUENCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP SEQUENCE statement
- sequence number object, dropping
ms.assetid: c25772d3-61af-4aa7-b58b-a6f67a793e3d
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d7247c5e809c8e26fbd17dc01e8c2f624a170ff
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-sequence-transact-sql"></a>ドロップ シーケンス (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  現在のデータベースからシーケンス オブジェクトを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DROP SEQUENCE [ IF EXISTS ] { [ database_name . [ schema_name ] . | schema_name. ]    sequence_name } [ ,...n ]  
 [ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *場合に存在します。*  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
 条件付きでは既に存在する場合にのみ、シーケンスを削除します。  
  
 *database_name*  
 シーケンス オブジェクトが作成されたデータベースの名前を指定します。  
  
 *schema_name*  
 シーケンス オブジェクトが所属するスキーマの名前を指定します。  
  
 *sequence_name*  
 削除するシーケンスの名前です。 種類は**sysname**です。  
  
## <a name="remarks"></a>解説  
 番号の生成後、その番号とシーケンス オブジェクトは無関係になるため、生成された番号が使用されている場合でも、シーケンス オブジェクトは削除できます。  
  
 シーケンス オブジェクトはスキーマ バインドされないため、ストアド プロシージャまたはトリガーによって参照されているシーケンス オブジェクトは削除できます。 テーブルで既定値として参照されているシーケンス オブジェクトは削除できません。 シーケンスを参照しているオブジェクトの一覧がエラー メッセージに表示されます。  
  
 データベース内のすべてのシーケンス オブジェクトを一覧表示するには、次のステートメントを実行します。  
  
```  
SELECT sch.name + '.' + seq.name AS [Sequence schema and name]   
    FROM sys.sequences AS seq  
    JOIN sys.schemas AS sch  
        ON seq.schema_id = sch.schema_id ;  
GO  
```  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 スキーマに対する ALTER または CONTROL 権限が必要です。  
  
### <a name="audit"></a>監査  
 監査する**DROP SEQUENCE**、モニター、 **SCHEMA_OBJECT_CHANGE_GROUP**です。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のデータベースから `CountBy1` という名前のシーケンス オブジェクトを削除します。  
  
```  
DROP SEQUENCE CountBy1 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER SEQUENCE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [SEQUENCE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-sequence-transact-sql.md)   
 [次の値を & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/next-value-for-transact-sql.md)   
 [シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  

