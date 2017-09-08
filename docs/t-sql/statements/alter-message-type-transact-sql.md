---
title: "メッセージ型 (TRANSACT-SQL) を ALTER |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_MESSAGE_TYPE_TSQL
- ALTER MESSAGE TYPE
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER MESSAGE TYPE statement
- modifying message types
- message types [Service Broker], modifying
ms.assetid: 98c94176-2bdf-4725-b4bc-d33b6b14817d
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1ed67afafb33faa22ececbea51c1ed502b1e5725
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-message-type-transact-sql"></a>ALTER MESSAGE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  メッセージ型のプロパティを変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER MESSAGE TYPE message_type_name  
   VALIDATION =  
    {  NONE   
     | EMPTY   
     | WELL_FORMED_XML   
     | VALID_XML WITH SCHEMA COLLECTION schema_collection_name }  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *message_type_name*  
 変更するメッセージ型の名前を指定します。 サーバー名、データベース名、スキーマ名は指定できません。  
  
 VALIDATION   
 指定方法[!INCLUDE[ssSB](../../includes/sssb-md.md)]この種類のメッセージのメッセージ本文を検証します。  
  
 なし  
 検証が実行されません。 メッセージ本文は、任意のデータが含まれます。 または NULL にすることがあります。  
  
 EMPTY  
 メッセージの本文は NULL であることが必要です。  
  
 WELL_FORMED_XML   
 メッセージの本文には、整形式の XML が含まれている必要があります。  
  
 VALID_XML_WITH_SCHEMA = *schema_collection_name*  
 メッセージの本文には、指定されたスキーマ コレクションのスキーマに準拠する XML が含まれている必要があります。 *Schema_collection_name*既存の XML スキーマ コレクションの名前を指定する必要があります。  
  
## <a name="remarks"></a>解説  
 メッセージ型の検証を変更しても、既にキューに配布されているメッセージには影響しません。  
  
 メッセージ型の AUTHORIZATION を変更するには、ALTER AUTHORIZATION ステートメントを使用します。  
  
## <a name="permissions"></a>Permissions  
 メッセージの種類を変更するためのアクセス許可の既定では、メッセージの種類のメンバーの所有者、 **db_ddladmin**または**db_owner**固定データベース ロールのメンバー、 **sysadmin**固定サーバー ロール。  
  
 ALTER MESSAGE TYPE ステートメントがスキーマ コレクションを指定する場合、ステートメントを実行するユーザーは、指定されているスキーマ コレクションに対する REFERENCES 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、メッセージの種類を変更`//Adventure-Works.com/Expenses/SubmitExpense`をメッセージ本文が整形式 XML ドキュメントを含めることが必要です。  
  
```  
ALTER MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]  
    VALIDATION = WELL_FORMED_XML ;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER AUTHORIZATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [メッセージの種類 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-message-type-transact-sql.md)   
 [メッセージの種類 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-message-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
