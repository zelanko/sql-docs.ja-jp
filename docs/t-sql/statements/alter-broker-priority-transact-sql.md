---
title: "ALTER BROKER PRIORITY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
- ALTER_BROKER_TSQL
- ALTER BROKER PRIORITY
- ALTER BROKER
- ALTER_BROKER_PRIORITY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER BROKER PRIORITY statement
- ssbdiagnose
ms.assetid: 15fda1b2-e4dd-4f9d-935a-2e38926075b2
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 833c0bed38d02905b3a260f50824825c9859484f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="alter-broker-priority-transact-sql"></a>ALTER BROKER PRIORITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  プロパティを変更、[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージ交換の優先度。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER BROKER PRIORITY ConversationPriorityName  
FOR CONVERSATION  
{ SET ( [ CONTRACT_NAME = {ContractName | ANY } ]  
        [ [ , ] LOCAL_SERVICE_NAME = {LocalServiceName | ANY } ]  
        [ [ , ] REMOTE_SERVICE_NAME = {'RemoteServiceName' | ANY } ]  
        [ [ , ] PRIORITY_LEVEL = { PriorityValue | DEFAULT } ]  
              )  
}  
[;]  
  
```  
  
## <a name="arguments"></a>引数  
 *ConversationPriorityName*  
 変更するメッセージ交換の優先度の名前を指定します。 名前は、現在のデータベース内のメッセージ交換の優先度を参照する必要があります。  
  
 SET  
 指定したメッセージ交換の優先度をメッセージ交換に適用するかどうかを決定するための条件を指定します。 SET は必須で、CONTRACT_NAME、LOCAL_SERVICE_NAME、REMOTE_SERVICE_NAME、または PRIORITY_LEVEL の各条件のうち、少なくとも 1 つを指定する必要があります。  
  
 CONTRACT_NAME = {*ContractName* | **ANY**}  
 メッセージ交換の優先度をメッセージ交換に適用するかどうかを決定するための条件として使用するコントラクトの名前を指定します。 *ContractName*は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]識別子、し、現在のデータベースで、コントラクトの名前を指定する必要があります。  
  
 *ContractName*  
 メッセージ交換の優先度をメッセージ交換を開始した BEGIN DIALOG ステートメントで ON CONTRACT が指定されているメッセージ交換にのみ適用できることを示す*ContractName*です。  
  
 ANY  
 使用するコントラクトに関係なく、メッセージ交換の優先度をどのメッセージ交換にも適用できることを指定します。  
  
 CONTRACT_NAME を指定しない場合、メッセージ交換の優先度のコントラクト プロパティは変更されません。  
  
 LOCAL_SERVICE_NAME = {*LocalServiceName* | **ANY**}  
 メッセージ交換の優先度をメッセージ交換のエンドポイントに適用するかどうかを決定するための条件として使用するサービスの名前を指定します。  
  
 *LocalServiceName*は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]識別子し、現在のデータベースで、サービスの名前を指定する必要があります。  
  
 *LocalServiceName*  
 メッセージ交換の優先度を次のメッセージ交換のエンドポイントに適用できることを指定します。  
  
-   発信側サービスの名前が一致する任意の発信側メッセージ交換エンドポイント*LocalServiceName*です。  
  
-   ターゲット サービスの名前が一致する任意のターゲット メッセージ交換エンドポイント*LocalServiceName*です。  
  
 ANY  
 -   エンドポイントで使用されるローカル サービスの名前に関係なく、メッセージ交換の優先度をどのメッセージ交換のエンドポイントにも適用できることを指定します。  
  
 LOCAL_SERVICE_NAME を指定しない場合、メッセージ交換の優先度のローカル サービス プロパティは変更されません。  
  
 REMOTE_SERVICE_NAME = {'*RemoteServiceName*' | **ANY**}  
 メッセージ交換の優先度をメッセージ交換のエンドポイントに適用するかどうかを決定するための条件として使用するサービスの名前を指定します。  
  
 *RemoteServiceName*型のリテラルは、 **nvarchar (256)**です。 [!INCLUDE[ssSB](../../includes/sssb-md.md)]一致するように、バイトごとの比較を使用して、 *RemoteServiceName*文字列。 この比較では、大文字と小文字が区別され、現在の照合順序は考慮されません。 現在のインスタンスで、ターゲット サービスができる、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、またはリモート インスタンス、[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。  
  
 '*RemoteServiceName*'  
 メッセージ交換の優先度を次のメッセージ交換のエンドポイントに割り当てることを指定します。  
  
-   関連付けられたターゲット サービスの名前が一致する任意の発信側メッセージ交換エンドポイント*RemoteServiceName*です。  
  
-   関連付けられている発信側サービスの名前が一致する任意のターゲット メッセージ交換エンドポイント*RemoteServiceName*です。  
  
 ANY  
 エンドポイントに関連付けられているリモート サービスの名前に関係なく、メッセージ交換の優先度をどのメッセージ交換のエンドポイントにも適用することを指定します。  
  
 REMOTE_SERVICE_NAME を指定しない場合、メッセージ交換の優先度のリモート サービス プロパティは変更されません。  
  
 Priority_level の各 = { *PriorityValue* | **既定**}  
 メッセージ交換の優先度で指定されているコントラクトおよびサービスを使用するすべてのメッセージ交換のエンドポイントに割り当てる優先度レベルを指定します。 *PriorityValue*リテラル 1 (最低優先順位) から 10 (最も高い優先度) を整数でなければなりません。  
  
 PRIORITY_LEVEL を指定しない場合、メッセージ交換の優先度の優先度レベル プロパティは変更されません。  
  
## <a name="remarks"></a>解説  
 ALTER BROKER PRIORITY で変更されるプロパティは、既存のメッセージ交換には適用されません。 既存のメッセージ交換は、開始されたときに割り当てられた優先度のままです。  
  
 詳細については、次を参照してください。 [CREATE BROKER PRIORITY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-broker-priority-transact-sql.md).  
  
## <a name="permissions"></a>権限  
 メッセージ交換の優先度のメンバに既定値を作成するためのアクセス許可、 **db_ddladmin**または**db_owner**固定データベース ロール、および、 **sysadmin**固定サーバー ロール。 データベースに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-only-the-priority-level-of-an-existing-conversation-priority"></a>A. 既存のメッセージ交換の優先度レベルのみ変更する  
 優先度レベルを変更しますが、コントラクト、ローカル サービス、またはリモート サービスの各プロパティは変更しません。  
  
```  
ALTER BROKER PRIORITY SimpleContractDefaultPriority  
    FOR CONVERSATION  
    SET (PRIORITY_LEVEL = 3);  
```  
  
### <a name="b-changing-all-of-the-properties-of-an-existing-conversation-priority"></a>B. 既存のメッセージ交換の優先度のプロパティをすべて変更する  
 優先度レベル、コントラクト、ローカル サービス、およびリモート サービスの各プロパティを変更します。  
  
```  
ALTER BROKER PRIORITY SimpleContractPriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = SimpleContractB,  
         LOCAL_SERVICE_NAME = TargetServiceB,  
         REMOTE_SERVICE_NAME = N'InitiatorServiceB',  
         PRIORITY_LEVEL = 8);  
```  
  
## <a name="see-also"></a>参照  
 [ブローカーの優先順位 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-broker-priority-transact-sql.md)   
 [DROP BROKER PRIORITY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-broker-priority-transact-sql.md)   
 [sys.conversation_priorities &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-conversation-priorities-transact-sql.md)  
  
  
