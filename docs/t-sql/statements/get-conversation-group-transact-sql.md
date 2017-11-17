---
title: "GET CONVERSATION GROUP (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GET
- CONVERSATION_GROUP_TSQL
- GET_TSQL
- GET_CONVERSATION_GROUP_TSQL
- GET CONVERSATION GROUP
- CONVERSATION GROUP
- GET CONVERSATION
- GET_CONVERSATION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GET CONVERSATION GROUP statement
- conversations [Service Broker], groups
ms.assetid: 4da8a855-33c0-43b2-a49d-527487cb3b5c
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5cf1bd19e9ccc290c2c822ab59f00be75d447ba1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="get-conversation-group-transact-sql"></a>GET CONVERSATION GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  次に受信するメッセージのメッセージ交換グループの識別子を返すと共に、そのメッセージが含まれるメッセージ交換のメッセージ交換グループをロックします。 メッセージ交換グループの識別子は、メッセージ自体を取得する前にメッセージ交換の状態情報を取得する場合に使用できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
[ WAITFOR ( ]  
   GET CONVERSATION GROUP @conversation_group_id  
      FROM <queue>  
[ ) ] [ , TIMEOUT timeout ]  
[ ; ]  
  
<queue> ::=  
{  
    [ database_name . [ schema_name ] . | schema_name . ] queue_name  
}  
```  
  
## <a name="arguments"></a>引数  
 WAITFOR  
 現在メッセージが存在しない場合、GET CONVERSATION GROUP ステートメントは、キューにメッセージが到着するのを待機します。  
  
 *@conversation_group_id*  
 GET CONVERSATION GROUP ステートメントによって返されるメッセージ交換グループ ID が格納される変数です。 型の変数がある必要があります**uniqueidentifier**です。 使用できるメッセージ交換グループがない場合、この変数は NULL に設定されます。  
  
 FROM  
 メッセージ交換グループを取得するキューを指定します。  
  
 *database_name*  
 メッセージ交換グループを取得するキューが含まれているデータベースの名前を指定します。 ない場合*database_name*が提供される、既定値は、現在のデータベースです。  
  
 *schema_name*  
 メッセージ交換グループを取得するキューを所有するスキーマの名前を指定します。 ない場合*schema_name*が提供される、既定値は、現在のユーザーの既定のスキーマです。  
  
 *queue_name*  
 メッセージ交換グループを取得するキューの名前を指定します。  
  
 タイムアウト*タイムアウト*  
 Service Broker が、キューにメッセージが到着するのを待機する時間を指定します (ミリ秒単位)。 この句は WAITFOR 句と共に使用する必要があります。 WAITFOR を使用するステートメントにこの句が含まれていない場合、または*タイムアウト*-1 で、待機時間は無制限です。 タイムアウトになると、GET CONVERSATION GROUP の設定、  *@conversation_group_id* 変数を NULL にします。  
  
## <a name="remarks"></a>解説  
  
> [!IMPORTANT]  
>  前のステートメントをセミコロンで終了する必要があります、GET CONVERSATION GROUP ステートメントがバッチまたはストアド プロシージャの最初のステートメントでない場合 (**;**) では、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントのターミネータです。  
  
 GET CONVERSATION GROUP ステートメントで指定したキューが使用できない場合、ステートメントは失敗し、[!INCLUDE[tsql](../../includes/tsql-md.md)] エラーが返されます。  
  
 このステートメントでは、以下の条件をすべて満たす、次に使用できるメッセージ交換グループが返されます。  
  
-   メッセージ交換グループを正常にロックできる。  
  
-   メッセージ交換グループに、キューで利用できるメッセージが含まれている。  
  
-   返されるメッセージ交換グループが、上記の条件を満たすすべてのメッセージ交換グループのうち、最も高い優先度を持つ。 メッセージ交換グループの優先度は、そのグループのメンバーであり、キュー内にメッセージがあるメッセージ交換のいずれかに割り当てられている最も高い優先度です。  
  
 同じトランザクション内で GET CONVERSATION GROUP を続けて呼び出すと、複数のメッセージ交換グループがロックされる場合があります。 使用できるメッセージ交換グループがない場合、このステートメントでは、メッセージ交換グループの識別子として NULL が返されます。  
  
 WAITFOR 句を指定した場合、ステートメントは指定のタイムアウト時間が経過するかメッセージ交換グループが使用できるようになるまで待機します。 ステートメントの待機中にキューが削除された場合は、その時点でエラーが返されます。  
  
 GET CONVERSATION GROUP は、ユーザー定義の関数では無効です。  
  
## <a name="permissions"></a>Permissions  
 メッセージ交換グループの識別子をキューから取得する場合、現在のユーザーは、そのキューに対する RECEIVE 権限を持っている必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-getting-a-conversation-group-waiting-indefinitely"></a>A. 無制限に待機して、メッセージ交換グループを取得する  
 次の例では、`@conversation_group_id` にメッセージ交換グループの識別子を設定します。このメッセージ交換グループは、`ExpenseQueue` 上にあり、次に使用できるメッセージで使用されます。 このコマンドは、メッセージが使用できるようになるまで待機します。  
  
```  
DECLARE @conversation_group_id UNIQUEIDENTIFIER ;  
  
WAITFOR (  
 GET CONVERSATION GROUP @conversation_group_id  
     FROM ExpenseQueue  
) ;  
```  
  
### <a name="b-getting-a-conversation-group-waiting-one-minute"></a>B. 1 分間待機して、メッセージ交換グループを取得する  
 次の例では、`@conversation_group_id` にメッセージ交換グループの識別子を設定します。このメッセージ交換グループは、`ExpenseQueue` 上にあり、次に使用できるメッセージで使用されます。 使用できるメッセージが 1 分以内に取得できない場合、GET CONVERSATION GROUP では、`@conversation_group_id` の値が変更されずに返されます。  
  
```  
DECLARE @conversation_group_id UNIQUEIDENTIFIER  
  
WAITFOR (  
    GET CONVERSATION GROUP @conversation_group_id   
    FROM ExpenseQueue ),  
TIMEOUT 60000 ;  
```  
  
### <a name="c-getting-a-conversation-group-returning-immediately"></a>C. 待機せず、メッセージ交換グループを取得する  
 次の例では、`@conversation_group_id` にメッセージ交換グループの識別子を設定します。このメッセージ交換グループは、`ExpenseQueue` 上にあり、次に使用できるメッセージで使用されます。 メッセージが使用できない場合`GET CONVERSATION GROUP`変更せずにすぐに返す`@conversation_group_id`です。  
  
```  
DECLARE @conversation_group_id UNIQUEIDENTIFIER ;  
  
GET CONVERSATION GROUP @conversation_group_id  
FROM AdventureWorks.dbo.ExpenseQueue ;  
```  
  
## <a name="see-also"></a>参照  
 [BEGIN DIALOG CONVERSATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [メッセージ交換の移動 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/move-conversation-transact-sql.md)  
  
  

