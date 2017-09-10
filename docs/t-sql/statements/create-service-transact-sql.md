---
title: "サービス (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f281cd0f60c0f4f2a37419af4870d927868183a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-service-transact-sql"></a>CREATE SERVICE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 作成するサービスの名前を指定します。 新しいサービスは現在のデータベースで作成され、AUTHORIZATION 句で指定されるプリンシパルによって所有されます。 サーバー名、データベース名、スキーマ名は指定できません。 *Service_name*は有効な**sysname**です。  
  
> [!NOTE]  
>  作成しないキーワードを使用するサービスのいずれか、 *service_name*です。 CREATE BROKER PRIORITY でサービス名に ANY を指定した場合、優先度はすべてのサービスに適用されます。 名前が ANY であるサービスに限定されません。  
  
 承認*owner_name*  
 サービスの所有者を、指定したデータベース ユーザーまたはロールに設定します。 現在のユーザーの場合は**dbo**または**sa**、 *owner_name*任意の有効なユーザーまたはロールの名前にすることがあります。 それ以外の場合、 *owner_name*現在のユーザーの名前、現在のユーザーが、IMPERSONATE 権限を持っているユーザーの名前または現在のユーザーが所属するロールの名前にする必要があります。  
  
 ON のキュー [ *schema_name***です。** *queue_name*  
 サービス用のメッセージを受信するキューを指定します。 キューはサービスと同じデータベース内に存在する必要があります。 ない場合は*schema_name*は提供された場合、スキーマは、ステートメントを実行するユーザーの既定のスキーマです。  
  
 *contract_name*  
 このサービスのコントラクトを指定します。 サービス プログラムでは、指定したコントラクトを使用して、サービスに対するメッセージ交換が開始されます。 コントラクトを指定しない場合、サービスではメッセージ交換が開始されるだけです。  
  
 **[**既定**]**  
 サービスは、DEFAULT コントラクトに従ったメッセージ交換の発信先となります。 この句のコンテキストでは、DEFAULT はキーワードとして扱われないため、識別子として区切り記号で区切る必要があります。 DEFAULT コントラクトでは、メッセージ交換の両側で DEFAULT メッセージ型のメッセージを送信できます。 DEFAULT メッセージ型では、検証は NONE となります。  
  
## <a name="remarks"></a>解説  
 各サービスでは、関連付けられているコントラクトで提供される機能が、他のサービスでも使用できるよう公開されます。 CREATE SERVICE ステートメントでは、サービスに対するコントラクトを指定できます。 サービスは、指定されたコントラクトを使用するメッセージ交換の発信先となります。 コントラクトを指定しないサービスの機能は、他のサービスに公開されません。  
  
 サービスで開始されるメッセージ交換では、任意のコントラクトを使用できます。 サービスでメッセージ交換を開始するだけの場合は、コントラクトを指定しないでサービスを作成できます。  
  
 ときに[!INCLUDE[ssSB](../../includes/sssb-md.md)]新しいメッセージ交換を受け入れるリモート サービスから発信先サービスの名前が、ブローカーがメッセージ交換のメッセージを配置する場所のキューを決定します。  
  
## <a name="permissions"></a>Permissions  
 メンバーにサービスを作成するアクセス許可が既定で、 **db_ddladmin**または**db_owner**固定データベース ロールおよび**sysadmin**固定サーバー ロール。 CREATE SERVICE ステートメントを実行するには、指定したキューとすべてのコントラクトに対して REFERENCES 権限が必要です。  
  
 サービスに対する REFERENCES 権限は、既定では、サービスのメンバーの所有者、 **db_ddladmin**または**db_owner**固定データベース ロールのメンバー、 **sysadmin**固定サーバー ロール。 サービスのメンバーの所有者に、サービスの既定値の送信のアクセス許可、 **db_owner**固定データベース ロールのメンバー、 **sysadmin**固定サーバー ロール。  
  
 サービスは一時オブジェクトとして指定できません。 始まるサービス名 **#** 許可されますが、パーマネント オブジェクト。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-service-with-one-contract"></a>A. 1 つのコントラクトでサービスを作成する  
 次の例は、サービスを作成`//Adventure-Works.com/Expenses`上、`ExpenseQueue`のキュー、`dbo`スキーマです。 このサービスを対象とするダイアログ ボックスは、コントラクトに従う必要があります`//Adventure-Works.com/Expenses/ExpenseSubmission`です。  
  
```  
CREATE SERVICE [//Adventure-Works.com/Expenses]  
    ON QUEUE [dbo].[ExpenseQueue]  
    ([//Adventure-Works.com/Expenses/ExpenseSubmission]) ;  
```  
  
### <a name="b-creating-a-service-with-multiple-contracts"></a>B. 複数のコントラクトでサービスを作成する  
 次の例では、`//Adventure-Works.com/Expenses` キューにサービス `ExpenseQueue` を作成します。 このサービスを対象とするダイアログ ボックスでは、コントラクトを従う必要がありますか、`//Adventure-Works.com/Expenses/ExpenseSubmission`またはコントラクト`//Adventure-Works.com/Expenses/ExpenseProcessing`です。  
  
```  
CREATE SERVICE [//Adventure-Works.com/Expenses] ON QUEUE ExpenseQueue  
    ([//Adventure-Works.com/Expenses/ExpenseSubmission],  
     [//Adventure-Works.com/Expenses/ExpenseProcessing]) ;  
```  
  
### <a name="c-creating-a-service-with-no-contracts"></a>C. コントラクトなしでサービスを作成する  
 次の例は、サービスを作成`//Adventure-Works.com/Expenses on the ExpenseQueue`キュー。 このサービスにはコントラクト情報はありません。 したがって、このサービスはダイアログの開始だけを行えます。  
  
```  
CREATE SERVICE [//Adventure-Works.com/Expenses] ON QUEUE ExpenseQueue ;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER SERVICE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-service-transact-sql.md)   
 [サービス &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-service-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
