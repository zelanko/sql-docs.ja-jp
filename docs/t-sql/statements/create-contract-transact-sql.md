---
title: "コントラクト (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
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
- CONTRACT_TSQL
- CREATE_CONTRACT_TSQL
- CREATE CONTRACT
- CONTRACT
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE CONTRACT statement
- contracts [Service Broker], creating
- message types [Service Broker], contracts
ms.assetid: 494cbfa6-8e93-4161-a64d-90d681915211
caps.latest.revision: 48
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 962ce2d6568a597bd580f7fc9bcd2e9243e44dc4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-contract-transact-sql"></a>CREATE CONTRACT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  新しいコントラクトを作成します。 コントラクトは、[!INCLUDE[ssSB](../../includes/sssb-md.md)] のメッセージ交換で使用されるメッセージ型を定義し、またメッセージ交換のどちら側がその型のメッセージを送信できるかを決定するものです。 各メッセージ交換は、コントラクトに従います。 発信側サービスでは、メッセージ交換の開始時に、そのメッセージ交換用のコントラクトを指定します。 発信先サービスでは、メッセージ交換を受け入れるコントラクトを指定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE CONTRACT contract_name  
   [ AUTHORIZATION owner_name ]  
      (  {   { message_type_name | [ DEFAULT ] }  
          SENT BY { INITIATOR | TARGET | ANY }   
       } [ ,...n] )   
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *contract_name*  
 作成するコントラクトの名前を指定します。 新しいコントラクトは現在のデータベースで作成され、AUTHORIZATION 句で指定するプリンシパルによって所有されます。 サーバー名、データベース名、スキーマ名は指定できません。 *Contract_name*には最大 128 文字にすることができます。  
  
> [!NOTE]  
>  作成しないキーワードを使用するコントラクトのいずれか、 *contract_name*です。 CREATE BROKER PRIORITY でコントラクト名に ANY を指定した場合、優先度はすべてのコントラクトに適用されます。 名前が ANY であるコントラクトに限定されません。  
  
 承認*owner_name*  
 コントラクトの所有者を、指定したデータベース ユーザーまたはロールに設定します。 現在のユーザーの場合は**dbo**または**sa**、 *owner_name*任意の有効なユーザーまたはロールの名前を指定できます。 それ以外の場合、 *owner_name*現在のユーザーの名前、現在のユーザーが持つ、権限を借用するユーザーの名前または現在のユーザーが所属するロールの名前にする必要があります。 この句を省略すると、コントラクトは現在のユーザーに属します。  
  
 *message_type_name*  
 コントラクトの一部として含まれる、メッセージ型の名前を指定します。  
  
 SENT BY  
 指定したメッセージ型のメッセージを送信できるエンドポイントを指定します。 コントラクトには、サービスが特定のメッセージ交換で使用できるメッセージが記録されています。 各メッセージ交換が 2 つのエンドポイント:*イニシエーター*エンドポイントで、メッセージ交換を開始するサービス、および*ターゲット*エンドポイント、サービス、発信側です。  
  
 INITIATOR   
 メッセージ交換の発信側だけが、指定したメッセージ型のメッセージを送信できることを示します。 メッセージ交換を開始するサービスと呼びます、*イニシエーター*メッセージ交換の発信します。  
  
 TARGET  
 メッセージ交換の発信先だけが、指定したメッセージ型のメッセージを送信できることを示します。 別のサービスによって開始されたメッセージ交換を受け付けるサービスと呼びます、*ターゲット*メッセージ交換の発信します。  
  
 ANY  
 指定した型のメッセージを、発信側と発信先の両方から送信できることを示します。  
  
 [ DEFAULT ]  
 コントラクトで、既定のメッセージ型のメッセージがサポートされることを示します。 既定では、すべてのデータベースに DEFAULT というメッセージ型が含まれます。 このメッセージ型では、NONE の検証が行われます。 この句のコンテキストでは、DEFAULT はキーワードとして扱われないため、識別子として区切り記号で区切る必要があります。 Microsoft SQL Server では、DEFAULT メッセージ型を指定する DEFAULT コントラクトも提供されています。  
  
## <a name="remarks"></a>解説  
 コントラクトのメッセージ型の順序は重要ではありません。 ターゲットが、最初のメッセージを受信した後[!INCLUDE[ssSB](../../includes/sssb-md.md)]をいつでもメッセージ交換の指定された側の許可されているすべてのメッセージを送信するメッセージ交換のどちらかの側を許可します。 たとえば、メッセージ交換の発信側がメッセージの種類を送信できます**//Adventure-Works.com/Expenses/SubmitExpense**、[!INCLUDE[ssSB](../../includes/sssb-md.md)]により、任意の数を送信するイニシエーター **SubmitExpense**中、メッセージ交換のメッセージ。  
  
 コントラクトのメッセージ型と送信方向は変更できません。 コントラクトの AUTHORIZATION を変更するには、ALTER AUTHORIZATION ステートメントを使用します。  
  
 コントラクトでは、発信側からのメッセージ送信が許可されている必要があります。 コントラクトに、SENT BY ANY または SENT BY INITIATOR のメッセージ型のうち少なくとも 1 つが含まれていないと、CREATE CONTRACT ステートメントは失敗します。  
  
 、コントラクトに関係なく、サービスは常にメッセージの種類を受信`http://schemas.microsoft.com/SQL/ServiceBroker/DialogTimer`、 `http://schemas.microsoft.com/SQL/ServiceBroker/Error`、および`http://schemas.microsoft.com/SQL/ServiceBroker/EndDialog`です。 [!INCLUDE[ssSB](../../includes/sssb-md.md)] では、アプリケーションへのシステム メッセージにこれらのメッセージ型が使用されます。  
  
 コントラクトは一時オブジェクトとして指定できません。 # で始まるコントラクト名は許可されますが、パーマネント オブジェクトになります。  
  
## <a name="permissions"></a>Permissions  
 既定では、メンバー、 **db_ddladmin**または**db_owner**固定データベース ロールおよび**sysadmin**固定サーバー ロールは、コントラクトを作成できます。  
  
 既定では、メンバーは、コントラクトの所有者、 **db_ddladmin**または**db_owner**固定データベース ロールのメンバー、 **sysadmin**固定サーバー ロールの参照があります。コントラクトの権限です。  
  
 CREATE CONTRACT ステートメントを実行するには、指定されているすべてのメッセージ型に対する REFERENCES 権限が必要です。  
  
## <a name="examples"></a>使用例  
 **A.コントラクトを作成します。**  
  
 次の例では、3 つのメッセージ型に基づいて費用返済のコントラクトを作成します。  
  
```  
CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]           
    VALIDATION = WELL_FORMED_XML ;           
  
CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/ExpenseApprovedOrDenied]           
    VALIDATION = WELL_FORMED_XML ;           
  
CREATE MESSAGE TYPE           
    [//Adventure-Works.com/Expenses/ExpenseReimbursed]           
    VALIDATION= WELL_FORMED_XML ;           
  
CREATE CONTRACT            
    [//Adventure-Works.com/Expenses/ExpenseSubmission]           
    ( [//Adventure-Works.com/Expenses/SubmitExpense]           
          SENT BY INITIATOR,           
      [//Adventure-Works.com/Expenses/ExpenseApprovedOrDenied]           
          SENT BY TARGET,           
      [//Adventure-Works.com/Expenses/ExpenseReimbursed]           
          SENT BY TARGET           
    ) ;  
```  
  
## <a name="see-also"></a>参照  
 [コントラクト &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-contract-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

