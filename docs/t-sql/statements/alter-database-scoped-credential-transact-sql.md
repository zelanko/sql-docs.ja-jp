---
title: "ALTER データベース スコープの資格情報 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER DATABASE SCOPED CREDENTIAL
- ALTER_DATABASE_SCOPED_CREDENTIAL_TSQL
helpviewer_keywords:
- ALTER DATABASE SCOPED CREDENTIAL statement
- credentials [SQL Server], ALTER DATABASE SCOPED CREDENTIAL statement
ms.assetid: 966b75b5-ca87-4203-8bf9-95c4e00cb0b5
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 91224c6e96fb3ee3962331ec6f378ea9aad1a5b5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-scoped-credential-transact-sql"></a>ALTER データベース スコープ ベースの資格情報 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  データベースのプロパティの変更には、資格情報がスコープ設定されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
```  
  
## <a name="arguments"></a>引数  
 *credential_name*  
 変更対象のデータベース スコープの資格情報の名前を指定します。  
  
 IDENTITY **='***identity_name***'**  
 サーバーの外部に接続するときに使用するアカウントの名前を指定します。 Azure Blob ストレージからファイルをインポートするユーザー名がある必要があります`SHARED ACCESS SIGNATURE`です。  共有アクセス署名の詳細については、次を参照してください。[を使用して共有アクセス署名 (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1)です。  
    
  
 シークレット**='***シークレット***'**  
 送信の認証に必要なシークレットを指定します。 *シークレット*Azure Blob ストレージからファイルをインポートするが必要です。 *シークレット*他の目的で省略可能な場合があります。   
>  [!WARNING]
>  SAS キーの値が始まる可能性があります、'?'(疑問符)。 SAS キーを使用する場合は、先頭を削除する必要があります '?' です。 それ以外の場合、作業がブロックされる可能性があります。    
  
## <a name="remarks"></a>解説  
 ときに、データベース スコープ資格情報は、変更、両方の値*identity_name*と*シークレット*リセットされます。 SECRET 引数を省略すると、格納されているシークレットの値は NULL に設定されます。  
  
 シークレットは、サービス マスター_キーを使用して暗号化されます。 サービス マスター キーが再生成された場合、シークレットは新しいサービス マスター キーを使って再暗号化されます。  
  
 データベース スコープ資格情報に関する情報は、 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)カタログ ビューです。  
  
## <a name="permissions"></a>Permissions  
 必要があります`ALTER`資格情報に対する権限。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-the-password-of-a-database-scoped-credential"></a>A. 資格情報をスコープするデータベースのパスワードを変更します。  
 次の例と呼ばれるデータベース スコープ資格情報に格納されているシークレットを変更する`Saddles`です。 データベース スコープ資格情報には、Windows ログインが含まれています。`RettigB`とそのパスワードです。 新しいパスワードには、SECRET 句を使用して、データベース スコープの資格情報が追加されます。  
  
```  
ALTER DATABASE SCOPED CREDENTIAL AppCred WITH IDENTITY = 'RettigB',   
    SECRET = 'sdrlk8$40-dksli87nNN8';  
GO  
```  
  
### <a name="b-removing-the-password-from-a-credential"></a>B. 資格情報からパスワードを削除する  
 次の例は、名前付きデータベース スコープ資格情報からパスワードを削除`Frames`です。 データベース スコープ資格情報には、Windows ログインが含まれています。`Aboulrus8`とパスワード。 ステートメントを実行すると、後に、データベース スコープの資格情報は秘密のオプションが指定されていないためにパスワードは NULL があります。  
  
```  
ALTER DATABASE SCOPED CREDENTIAL Frames WITH IDENTITY = 'Aboulrus8';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [資格情報 (&) #40";"データベース エンジン"&"#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [データベース スコープの資格情報 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [データベース スコープの資格情報 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  

