---
title: "リモート サービス バインド (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE REMOTE SERVICE BINDING
- SERVICE_BINDING_TSQL
- CREATE REMOTE SERVICE
- REMOTE_TSQL
- CREATE_REMOTE_SERVICE_BINDING_TSQL
- CREATE_REMOTE_SERVICE_TSQL
- BINDING
- SERVICE BINDING
- BINDING_TSQL
- CREATE_REMOTE_TSQL
- REMOTE_SERVICE_TSQL
- CREATE REMOTE
- REMOTE SERVICE
- REMOTE_SERVICE_BINDING_TSQL
- REMOTE
- REMOTE SERVICE BINDING
dev_langs:
- TSQL
helpviewer_keywords:
- binding remote service [Service Broker]
- dialog security [Service Broker]
- end-to-end security [Service Broker]
- security [Service Broker], remote service bindings
- CREATE REMOTE SERVICE BINDING statement
- conversation security [Service Broker]
- remote service bindings [Service Broker], creating
ms.assetid: 4165c404-4d50-4063-9a6e-6e267d309376
caps.latest.revision: 46
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4083cb617d76084719450a6abc49fd76345cc7a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-remote-service-binding-transact-sql"></a>CREATE REMOTE SERVICE BINDING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  バインドを作成し、リモート サービスとのメッセージ交換を開始するときに使用するセキュリティ資格情報を定義します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE REMOTE SERVICE BINDING binding_name   
   [ AUTHORIZATION owner_name ]   
   TO SERVICE 'service_name'   
   WITH  USER = user_name [ , ANONYMOUS = { ON | OFF } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *binding_name*  
 作成するリモート サービス バインドの名前を指定します。 サーバー名、データベース名、スキーマ名は指定できません。 *Binding_name*は有効な**sysname**です。  
  
 承認*owner_name*  
 バインドの所有者を、指定したデータベース ユーザーまたはロールに設定します。 現在のユーザーの場合は**dbo**または**sa**、 *owner_name*任意の有効なユーザーまたはロールの名前を指定できます。 それ以外の場合、 *owner_name*現在のユーザーの名前、現在のユーザーが、IMPERSONATE 権限を持つユーザーの名前または現在のユーザーが所属するロールの名前にする必要があります。  
  
 サービスに '*service_name*'  
 WITH USER 句のユーザーにバインドするリモート サービスを指定します。  
  
 ユーザー = *user_name*  
 TO SERVICE 句のリモート サービスに関連付けられた証明を所有しているデータベース プリンシパルを指定します。 この証明は、リモート サービスと交換されるメッセージの暗号化と認証に使用されます。  
  
 ANONYMOUS  
 リモート サービスと通信するときに匿名認証を使用するかどうかを指定します。 Anonymous = ON の場合、匿名認証を使用してのメンバーとして、リモート データベースの操作が発生する、**パブリック**固定データベース ロール。 ANONYMOUS を OFF にすると、リモート データベースでの操作は、そのデータベース固有のユーザーによる操作として実行されます。 この句を指定しない場合、既定値は OFF になります。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)]リモート サービス バインドを使用して、新しいメッセージ交換に使用する証明書を見つけます。 関連付けられている証明書の公開キー *user_name*をリモート サービスに送信されるメッセージを認証し、メッセージ交換の暗号化を使用しているセッション キーの暗号化に使用します。 用の証明書*user_name*リモート サービスをホストするデータベース内のユーザーの証明書に対応する必要があります。  
  
 リモート サービス バインドは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの外部にある対象サービスと通信するサービスを開始する場合にのみ必要です。 開始サービスをホストするデータベースには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの外部にあるすべての対象サービスのリモート サービス バインドが含まれている必要があります。 ただし、対象サービスをホストするデータベースには、対象サービスと通信する開始サービスのリモート サービス バインドが含まれている必要はありません。 開始サービスと対象サービスが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の同じインスタンス内にある場合、リモート サービス バインドは必要ありません。 ただし、リモート サービス バインドが存在する場所である場合、 *service_name* 、ローカル サービスの名前に一致するサービスに対して指定された[!INCLUDE[ssSB](../../includes/sssb-md.md)]バインディングを使用します。  
  
 匿名 = ON の場合、発信側サービスのメンバーとして対象サービスに接続する、**パブリック**固定データベース ロール。 既定では、このロールのメンバーはデータベースに接続する権限を持ちません。 メッセージを正常に送信するには、ターゲット データベースを与える必要があります、**パブリック**ロール、データベースの CONNECT 権限と、ターゲット サービス用の SEND 権限です。  
  
 ユーザーが複数の証明を所有している場合は、[!INCLUDE[ssSB](../../includes/sssb-md.md)] によって現在有効な証明のうち有効期限が最も新しい証明が選択され、その証明が AVAILABLE FOR BEGIN_DIALOG としてマークされます。  
  
## <a name="permissions"></a>Permissions  
 リモートを作成するためのアクセス許可はサービスのメンバーである USER 句で指定されたユーザーへの既定のバインド、 **db_owner**のメンバー、固定データベース ロール、 **db_ddladmin**固定データベース ロール、およびメンバー**sysadmin**固定サーバー ロール。  
  
 CREATE REMOTE SERVICE BINDING ステートメントを実行するには、ステートメントで指定されるプリンシパルの借用権限が必要です。  
  
 リモート サービス バインドは一時オブジェクトとして指定できません。 始まるリモート サービス バインド名 **#** 許可されますが、パーマネント オブジェクト。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-remote-service-binding"></a>A. リモート サービス バインドを作成する  
 次の例は、サービスのバインドを作成`//Adventure-Works.com/services/AccountsPayable`です。 [!INCLUDE[ssSB](../../includes/sssb-md.md)] では、データベース プリンシパル `APUser` が所有する証明を使用してリモート サービスへの認証が行われ、リモート サービスとの間でセッション暗号化キーが交換されます。  
  
```  
CREATE REMOTE SERVICE BINDING APBinding  
    TO SERVICE '//Adventure-Works.com/services/AccountsPayable'  
    WITH USER = APUser ;  
```  
  
### <a name="b-creating-a-remote-service-binding-using-anonymous-authentication"></a>B. 匿名認証を使用してリモート サービス バインドを作成する  
 次の例は、サービスのバインドを作成`//Adventure-Works.com/services/AccountsPayable`です。 [!INCLUDE[ssSB](../../includes/sssb-md.md)] では、データベース プリンシパル `APUser` が所有する証明を使用して、リモート サービスとの間でセッション暗号化キーが交換されます。 Service Broker でリモート サービスへの認証は行われません。 として配信されるメッセージをリモート サービスをホストするデータベースで、**ゲスト**ユーザー。  
  
```  
CREATE REMOTE SERVICE BINDING APBinding  
    TO SERVICE '//Adventure-Works.com/services/AccountsPayable'  
    WITH USER = APUser, ANONYMOUS=ON ;  
```  
  
## <a name="see-also"></a>参照  
 [リモート サービス バインド &#40; を ALTER します。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-remote-service-binding-transact-sql.md)   
 [リモート サービス バインド &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-remote-service-binding-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

