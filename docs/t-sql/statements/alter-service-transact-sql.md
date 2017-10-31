---
title: "ALTER SERVICE (TRANSACT-SQL) |Microsoft ドキュメント"
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
- ALTER SERVICE
- ALTER_SERVICE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- modifying services
- contracts [Service Broker], modifying
- ALTER SERVICE statement
- services [Service Broker], modifying
ms.assetid: 2b4608f7-bb2e-4246-aa29-b52c55995b3a
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f0f09a018648566cd928258da958bb06dedc6022
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-service-transact-sql"></a>ALTER SERVICE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のサービスを変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER SERVICE service_name   
   [ ON QUEUE [ schema_name . ]queue_name ]   
   [ ( < opt_arg > [ , ...n ] ) ]  
[ ; ]  
  
<opt_arg> ::=  
   ADD CONTRACT contract_name | DROP CONTRACT contract_name  
```  
  
## <a name="arguments"></a>引数  
 *service_name*  
 変更するサービス名を指定します。 サーバー名、データベース名、スキーマ名は指定できません。  
  
 ON のキュー [ *schema_name***です。** *queue_name*  
 このサービス用の新しいキューを指定します。 [!INCLUDE[ssSB](../../includes/sssb-md.md)]このサービスのすべてのメッセージを現在のキューから新しいキューに移動します。  
  
 契約の追加*contract_name*  
 このサービスで公開されるコントラクト セットに追加するコントラクトを指定します。  
  
 DROP CONTRACT *contract_name*  
 このサービスで公開されるコントラクト セットから削除するコントラクトを指定します。 [!INCLUDE[ssSB](../../includes/sssb-md.md)]このコントラクトを使用する既存のメッセージ交換をこのサービスでエラー メッセージを送信します。  
  
## <a name="remarks"></a>解説  
 ALTER SERVICE ステートメントによってサービスからコントラクトが削除されると、サービスは、このコントラクトを使用するメッセージ交換の対象から除外されます。 したがって、[!INCLUDE[ssSB](../../includes/sssb-md.md)]そのコントラクトに新しいメッセージ交換をサービスにはできません。 このコントラクトを使用する既存のメッセージ交換に影響はありません。  
  
 サービスの AUTHORIZATION を変更するには、ALTER AUTHORIZATION ステートメントを使用します。  
  
## <a name="permissions"></a>Permissions  
 サービスを変更するためのアクセス許可の既定では、サービスのメンバーの所有者、 **db_ddladmin**または**db_owner**固定データベース ロールのメンバー、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-the-queue-for-a-service"></a>A. サービスのキューを変更する  
 次の例では、キュー `//Adventure-Works.com/Expenses` を使用するよう、`NewQueue` サービスを変更します。  
  
```  
ALTER SERVICE [//Adventure-Works.com/Expenses]  
    ON QUEUE NewQueue ;  
```  
  
### <a name="b-adding-a-new-contract-to-the-service"></a>B. サービスに新しいコントラクトを追加する  
 次の例の変更、`//Adventure-Works.com/Expenses`サービス コントラクトのダイアログを許可する`//Adventure-Works.com/Expenses`です。  
  
```  
ALTER SERVICE [//Adventure-Works.com/Expenses]  
    (ADD CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]) ;  
```  
  
### <a name="c-adding-a-new-contract-to-the-service-dropping-existing-contract"></a>C. サービスに新しいコントラクトを追加し、既存のコントラクトを削除する  
 次の例では、コントラクト `//Adventure-Works.com/Expenses` のダイアログを許可し、コントラクト `//Adventure-Works.com/Expenses/ExpenseProcessing` のダイアログを禁止するよう、`//Adventure-Works.com/Expenses/ExpenseSubmission` サービスを変更します。  
  
```  
ALTER SERVICE [//Adventure-Works.com/Expenses]  
    (ADD CONTRACT [//Adventure-Works.com/Expenses/ExpenseProcessing],   
     DROP CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]) ;  
```  
  
## <a name="see-also"></a>参照  
 [CREATE SERVICE &#40;Transact-SQL&#41;](../../t-sql/statements/create-service-transact-sql.md)   
 [サービス &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-service-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

