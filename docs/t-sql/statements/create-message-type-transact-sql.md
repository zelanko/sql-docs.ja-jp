---
title: "メッセージ型 (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_MESSAGE_TSQL
- MESSAGE_TSQL
- MESSAGE
- CREATE MESSAGE
- CREATE_MESSAGE_TYPE_TSQL
- MESSAGE TYPE
- MESSAGE_TYPE_TSQL
- CREATE MESSAGE TYPE
dev_langs: TSQL
helpviewer_keywords:
- XML [Service Broker]
- validation [Service Broker]
- message types [Service Broker], creating
- empty messages [SQL Server]
- binary [SQL Server], message types
- CREATE MESSAGE TYPE statement
ms.assetid: 98fe0fff-1a2e-4ca2-b37f-83a06fdf098e
caps.latest.revision: "41"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 78606c8f9f058acec660a7fe20a392f93c8dee49
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="create-message-type-transact-sql"></a>CREATE MESSAGE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  新しいメッセージ型を作成します。 メッセージの種類は、メッセージと検証の名前を定義する[!INCLUDE[ssSB](../../includes/sssb-md.md)]をその名前を持つメッセージを実行します。 メッセージ交換の両側で、同じメッセージ型を定義する必要があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE MESSAGE TYPE message_type_name  
    [ AUTHORIZATION owner_name ]  
    [ VALIDATION = {  NONE  
                    | EMPTY   
                    | WELL_FORMED_XML  
                    | VALID_XML WITH SCHEMA COLLECTION schema_collection_name  
                   } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *message_type_name*  
 作成するメッセージ型の名前を指定します。 新しいメッセージ型が現在のデータベースで作成され、AUTHORIZATION 句で指定されるプリンシパルによって所有されます。 サーバー名、データベース名、スキーマ名は指定できません。 *Message_type_name*には最大 128 文字にすることができます。  
  
 承認*owner_name*  
 メッセージ型の所有者を、指定したデータベース ユーザーまたはロールに設定します。 現在のユーザーの場合は**dbo**または**sa**、 *owner_name*任意の有効なユーザーまたはロールの名前を指定できます。 それ以外の場合、 *owner_name*現在のユーザーの名前、現在のユーザーが、IMPERSONATE 権限を持つユーザーの名前または現在のユーザーが所属するロールの名前にする必要があります。 この句を省略すると、メッセージ型は現在のユーザーに属します。  
  
 VALIDATION   
 指定方法[!INCLUDE[ssSB](../../includes/sssb-md.md)]この種類のメッセージのメッセージ本文を検証します。 この句を指定しない場合、検証は既定で NONE に設定されます。  
  
 なし  
 検証を実行しないことを指定します。 メッセージの本文にはなんらかのデータが含まれているか、NULL の可能性があります。  
  
 EMPTY  
 メッセージの本文は NULL にする必要があることを指定します。  
  
 WELL_FORMED_XML   
 メッセージの本文に、整形式の XML が含まれている必要があることを指定します。  
  
 VALID_XML WITH SCHEMA COLLECTION *schema_collection_name*  
 メッセージ本文が指定されたスキーマ コレクション内のスキーマに準拠する XML を含める必要がありますを指定します、 *schema_collection_name*既存の XML スキーマ コレクションの名前を指定する必要があります。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)]受信メッセージを検証します。 メッセージに、指定された検証の種類に準拠しないメッセージの本文が含まれている場合、[!INCLUDE[ssSB](../../includes/sssb-md.md)] によって無効なメッセージが破棄され、メッセージを送信したサービスにエラー メッセージが返されます。  
  
 メッセージ交換の両側で、メッセージ型に同じ名前を定義する必要があります。 [!INCLUDE[ssSB](../../includes/sssb-md.md)] では、メッセージ交換の両側で同じ検証を使用する必要はありませんが、トラブルシューティングで役立つように、通常はメッセージ交換の両側でメッセージ型に同じ検証を指定します。  
  
 メッセージ型は一時オブジェクトとして指定できません。 メッセージ型名で始まる **#** 許可されますが、パーマネント オブジェクト。  
  
## <a name="permissions"></a>Permissions  
 メッセージの種類のメンバーに既定値を作成するためのアクセス許可、 **db_ddladmin**または**db_owner**固定データベース ロールおよび**sysadmin**固定サーバー ロール。  
  
 メッセージ型に対する REFERENCES 権限の既定では、メッセージの種類のメンバーの所有者、 **db_owner**固定データベース ロールのメンバー、 **sysadmin**固定サーバー ロール。  
  
 CREATE MESSAGE TYPE ステートメントがスキーマ コレクションを指定する場合、ステートメントを実行するユーザーは、指定されているスキーマ コレクションに対する REFERENCES 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-message-type-containing-well-formed-xml"></a>A. 整形式の XML が含まれるメッセージ型を作成する  
 次の例では、整形式の XML が含まれる新しいメッセージ型を作成します。  
  
```  
CREATE MESSAGE TYPE  
  [//Adventure-Works.com/Expenses/SubmitExpense]  
  VALIDATION = WELL_FORMED_XML ;     
```  
  
### <a name="b-creating-a-message-type-containing-typed-xml"></a>B. 型指定された XML が含まれるメッセージ型を作成する  
 次の例では、XML でエンコードされた経費報告書に対するメッセージ型を作成します。 この例では、単純な経費報告書に対するスキーマを保持する XML スキーマ コレクションを作成します。 次に、スキーマに対するメッセージを検証する新しいメッセージ型を作成します。  
  
```  
CREATE XML SCHEMA COLLECTION ExpenseReportSchema AS  
N'<?xml version="1.0" encoding="UTF-16" ?>  
  <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
     targetNamespace="http://Adventure-Works.com/schemas/expenseReport"  
     xmlns:expense="http://Adventure-Works.com/schemas/expenseReport"  
     elementFormDefault="qualified"  
   >   
    <xsd:complexType name="expenseReportType">  
       <xsd:sequence>  
         <xsd:element name="EmployeeName" type="xsd:string"/>  
         <xsd:element name="EmployeeID" type="xsd:string"/>  
         <xsd:element name="ItemDetail"  
           type="expense:ItemDetailType" maxOccurs="unbounded"/>  
      </xsd:sequence>  
    </xsd:complexType>  
  
    <xsd:complexType name="ItemDetailType">  
      <xsd:sequence>  
        <xsd:element name="Date" type="xsd:date"/>  
        <xsd:element name="CostCenter" type="xsd:string"/>  
        <xsd:element name="Total" type="xsd:decimal"/>  
        <xsd:element name="Currency" type="xsd:string"/>  
        <xsd:element name="Description" type="xsd:string"/>  
      </xsd:sequence>  
    </xsd:complexType>  
  
    <xsd:element name="ExpenseReport" type="expense:expenseReportType"/>  
  
  </xsd:schema>' ;  
  
  CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]  
    VALIDATION = VALID_XML WITH SCHEMA COLLECTION ExpenseReportSchema ;  
```  
  
### <a name="c-creating-a-message-type-for-an-empty-message"></a>C. 空のメッセージに対するメッセージ型を作成する  
 次の例では、空のエンコードを使用して新しいメッセージ型を作成します。  
  
```  
CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]  
    VALIDATION = EMPTY ;  
```  
  
### <a name="d-creating-a-message-type-containing-binary-data"></a>D. バイナリ データが含まれるメッセージ型を作成する  
 次の例では、バイナリ データが含まれる新しいメッセージ型を作成します。 メッセージには XML 以外のデータが含まれるので、メッセージ型には `NONE` の検証型が指定されます。 この場合、この型のメッセージを受信するアプリケーションで、メッセージにデータが含まれ、このデータが目的の型であることを確認する必要があります。  
  
```  
CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/ReceiptImage]  
    VALIDATION = NONE ;  
```  
  
## <a name="see-also"></a>参照  
 [メッセージの種類 &#40; を ALTER します。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-message-type-transact-sql.md)   
 [メッセージの種類 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-message-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
