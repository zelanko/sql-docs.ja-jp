---
title: CREATE SERVICE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE_SERVICE_TSQL
- SERVICE
- CREATE SERVICE
- SERVICE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- services [Service Broker], creating
- CREATE SERVICE statement
- contracts [Service Broker], service creation
ms.assetid: fb804fa2-48eb-4878-a12f-4e0d5f4bc9e3
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 31e92f6c96b5e7cbb3da9f7dbc1b196c63d2dc8f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="create-service-transact-sql"></a>CREATE SERVICE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  新しいサービスを作成します。 [!INCLUDE[ssSB](../../includes/sssb-md.md)] サービスとは、特定のタスクまたはタスク セットの名前です。 [!INCLUDE[ssSB](../../includes/sssb-md.md)] ではサービスの名前を使用して、メッセージのルーティング、データベース内の正しいキューへのメッセージの配信、メッセージ交換のコントラクトの適用を行います。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE SERVICE service_name  
   [ AUTHORIZATION owner_name ]  
   ON QUEUE [ schema_name. ]queue_name  
   [ ( contract_name | [DEFAULT][ ,...n ] ) ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *service_name*  
 作成するサービスの名前を指定します。 新しいサービスは現在のデータベースで作成され、AUTHORIZATION 句で指定されるプリンシパルによって所有されます。 サーバー名、データベース名、スキーマ名は指定できません。 *service_name* は、有効な **sysname** でなければなりません。  
  
> [!NOTE]  
>  *service_name* にキーワード ANY を使用するサービスは作成しないでください。 CREATE BROKER PRIORITY でサービス名に ANY を指定した場合、優先度はすべてのサービスに適用されます。 名前が ANY であるサービスに限定されません。  
  
 AUTHORIZATION *owner_name*  
 サービスの所有者を、指定したデータベース ユーザーまたはロールに設定します。 現在のユーザーが **dbo** または **sa** の場合、*owner_name* には、任意の有効なユーザーまたはロールの名前を指定できます。 それ以外の場合、*owner_name* には、現在のユーザーの名前、現在のユーザーが IMPERSONATE 権限を持つユーザーの名前、または現在のユーザーが属するロールの名前を指定する必要があります。  
  
 ON QUEUE [ *schema_name***.** ] *queue_name*  
 サービス用のメッセージを受信するキューを指定します。 キューはサービスと同じデータベース内に存在する必要があります。 *schema_name* を指定しない場合は、ステートメントを実行するユーザーに既定のスキーマが使用されます。  
  
 *contract_name*  
 このサービスのコントラクトを指定します。 サービス プログラムでは、指定したコントラクトを使用して、サービスに対するメッセージ交換が開始されます。 コントラクトを指定しない場合、サービスではメッセージ交換が開始されるだけです。  
  
 **[** DEFAULT **]**  
 サービスは、DEFAULT コントラクトに従ったメッセージ交換の発信先となります。 この句のコンテキストでは、DEFAULT はキーワードとして扱われないため、識別子として区切り記号で区切る必要があります。 DEFAULT コントラクトでは、メッセージ交換の両側で DEFAULT メッセージ型のメッセージを送信できます。 DEFAULT メッセージ型では、検証は NONE となります。  
  
## <a name="remarks"></a>Remarks  
 各サービスでは、関連付けられているコントラクトで提供される機能が、他のサービスでも使用できるよう公開されます。 CREATE SERVICE ステートメントでは、サービスに対するコントラクトを指定できます。 サービスは、指定されたコントラクトを使用するメッセージ交換の発信先となります。 コントラクトを指定しないサービスの機能は、他のサービスに公開されません。  
  
 サービスで開始されるメッセージ交換では、任意のコントラクトを使用できます。 サービスでメッセージ交換を開始するだけの場合は、コントラクトを指定しないでサービスを作成できます。  
  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] でリモート サービスからの新しいメッセージ交換を受け入れるときには、発信先サービスの名前を基に、メッセージ交換のメッセージを格納するキューが決まります。  
  
## <a name="permissions"></a>アクセス許可  
 サービスを作成する権限は、既定では **db_ddladmin** 固定データベース ロールまたは **db_owner** 固定データベース ロールのメンバー、および **sysadmin** 固定サーバー ロールのメンバーに与えられています。 CREATE SERVICE ステートメントを実行するには、指定したキューとすべてのコントラクトに対して REFERENCES 権限が必要です。  
  
 サービスに対する REFERENCES 権限は、既定ではサービスの所有者、**db_ddladmin** 固定データベース ロールまたは **db_owner** 固定データベース ロールのメンバー、および **sysadmin** 固定サーバー ロールのメンバーに与えられています。 サービスに対する SEND 権限は、既定ではサービスの所有者、**db_owner** 固定データベース ロールのメンバー、および **sysadmin** 固定サーバー ロールのメンバーに与えられています。  
  
 サービスは一時オブジェクトとして指定できません。 **#** で始まるサービス名は許可されますが、パーマネント オブジェクトになります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-service-with-one-contract"></a>A. 1 つのコントラクトでサービスを作成する  
 次の例では、`dbo` スキーマの `ExpenseQueue` キューにサービス `//Adventure-Works.com/Expenses` を作成します。 このサービスを対象とするダイアログは、コントラクト `//Adventure-Works.com/Expenses/ExpenseSubmission` に従う必要があります。  
  
```  
CREATE SERVICE [//Adventure-Works.com/Expenses]  
    ON QUEUE [dbo].[ExpenseQueue]  
    ([//Adventure-Works.com/Expenses/ExpenseSubmission]) ;  
```  
  
### <a name="b-creating-a-service-with-multiple-contracts"></a>B. 複数のコントラクトでサービスを作成する  
 次の例では、`//Adventure-Works.com/Expenses` キューにサービス `ExpenseQueue` を作成します。 このサービスを対象とするダイアログは、コントラクト `//Adventure-Works.com/Expenses/ExpenseSubmission` またはコントラクト `//Adventure-Works.com/Expenses/ExpenseProcessing` に従う必要があります。  
  
```  
CREATE SERVICE [//Adventure-Works.com/Expenses] ON QUEUE ExpenseQueue  
    ([//Adventure-Works.com/Expenses/ExpenseSubmission],  
     [//Adventure-Works.com/Expenses/ExpenseProcessing]) ;  
```  
  
### <a name="c-creating-a-service-with-no-contracts"></a>C. コントラクトなしでサービスを作成する  
 次の例では、サービス `//Adventure-Works.com/Expenses on the ExpenseQueue` キューを作成します。 このサービスにはコントラクト情報はありません。 したがって、このサービスはダイアログの開始だけを行えます。  
  
```  
CREATE SERVICE [//Adventure-Works.com/Expenses] ON QUEUE ExpenseQueue ;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER SERVICE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-service-transact-sql.md)   
 [DROP SERVICE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-service-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
