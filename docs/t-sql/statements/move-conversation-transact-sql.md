---
title: "メッセージ交換の移動 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MOVE_CONVERSATION_TSQL
- MOVE CONVERSATION
- MOVE_TSQL
- MOVE
dev_langs:
- TSQL
helpviewer_keywords:
- moving conversations
- MOVE CONVERSATION statement
- relocating conversations
- conversations [Service Broker], groups
- conversations [Service Broker], moving
ms.assetid: 1da4d2c9-e767-434e-b49b-615711a7f626
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 31141afc0008b0c234a32c6c58d2d8d7b37ddadd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="move-conversation-transact-sql"></a>MOVE CONVERSATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  メッセージ交換を、別のメッセージ交換グループに移動します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
MOVE CONVERSATION conversation_handle  
   TO conversation_group_id  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *conversation_handle*  
 移動するメッセージ交換のメッセージ交換ハンドルを含む、変数または定数。 *conversation_handle*型でなければなりません**uniqueidentifier**です。  
  
 *Conversation_group_id*  
 メッセージ交換の移動先となるメッセージ交換グループの識別子を含む、変数または定数。 *conversation_group_id*型でなければなりません**uniqueidentifier**です。  
  
## <a name="remarks"></a>解説  
 MOVE CONVERSATION ステートメントで指定されたメッセージ交換の移動*conversation_handle*で識別されるメッセージ交換グループ*conversation_group_id*です。 同じキューに関連付けられているメッセージ交換グループ間でのみ、ダイアログをリダイレクトできます。  
  
> [!IMPORTANT]  
>  前のステートメントをセミコロンで終了する必要があります、MOVE CONVERSATION ステートメントがバッチまたはストアド プロシージャの最初のステートメントでない場合 (**;**) では、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントのターミネータです。  
  
 MOVE CONVERSATION ステートメントに関連付けられているメッセージ交換グループのロック*conversation_handle*とで指定されたメッセージ交換グループ*conversation_group_id*トランザクションまでステートメントを含むがコミットまたはロールバックします。  
  
 ユーザー定義の関数では、MOVE CONVERSATION は無効です。  
  
## <a name="permissions"></a>Permissions  
 メッセージ交換を移動するには、そのメッセージ交換およびメッセージ交換グループの所有者であるか、固定サーバー ロール sysadmin または固定データベース ロール db_owner のメンバーである必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、メッセージ交換を別のメッセージ交換グループに移動します。  
  
```  
DECLARE @conversation_handle UNIQUEIDENTIFIER,  
        @conversation_group_id UNIQUEIDENTIFIER ;  
  
SET @conversation_handle =  
    <retrieve conversation handle from database> ;  
SET @conversation_group_id =  
    <retrieve conversation group ID from database> ;  
  
MOVE CONVERSATION @conversation_handle TO @conversation_group_id ;  
```  
  
## <a name="see-also"></a>参照  
 [BEGIN DIALOG CONVERSATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [GET CONVERSATION GROUP & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/get-conversation-group-transact-sql.md)   
 [END CONVERSATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/end-conversation-transact-sql.md)   
 [sys.conversation_groups & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-conversation-groups-transact-sql.md)   
 [sys.conversation_endpoints & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql.md)  
  
  

