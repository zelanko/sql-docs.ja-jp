---
title: sp_addapprole (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addapprole_TSQL
- sp_addapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addapprole
ms.assetid: 24200295-9a54-4cab-9922-fb2e88632721
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 926876ae171180b8a148d80fdbc0d34de4d4af6b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spaddapprole-transact-sql"></a>sp_addapprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  アプリケーション ロールを現在のデータベースに追加します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用して[CREATE APPLICATION ROLE](../../t-sql/statements/create-application-role-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addapprole [ @rolename = ] 'role' , [ @password = ] 'password'  
```  
  
## <a name="arguments"></a>引数  
 [  **@rolename =** ] **'***ロール***'**  
 新しいアプリケーション ロールの名前を指定します。 *ロール*は**sysname**、既定値はありません。 *ロール*有効な識別子をする必要があるあり、現在のデータベースに既に存在することはできません。  
  
 アプリケーション ロール名の長さは 1 ～ 128 文字で、英字、記号、および数字を含めることができます。 ロール名が円記号を含めることはできません (\\) NULL または空の文字列 (") したりします。  
  
 [  **@password =** ] **'***パスワード***'**  
 アプリケーション ロールをアクティブにするために必要なパスワードを指定します。 *パスワード*は**sysname**、既定値はありません。 *パスワード*NULL にすることはできません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザー (およびロール) は、スキーマを完全に区別されません。 以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]スキーマは完全にロールを区別します。 この新しいアーキテクチャは CREATE APPLICATION ROLE の動作に反映されています。 このステートメントに置き換えられる**sp_addapprole**です。  
  
 以前のバージョンとの下位互換性を維持するために[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 **sp_addapprole**は次の処理します。  
  
-   アプリケーション ロールと同じ名前のスキーマが存在しない場合、同じ名前のスキーマが作成されます。 新しいスキーマは、アプリケーション ロールが所有し、そのアプリケーション ロールの既定のスキーマになります。  
  
-   アプリケーション ロールと同じ名前のスキーマが既に存在する場合、この処理は失敗します。  
  
-   パスワードの複雑性は確認されません**sp_addapprole**です。 ただし、CREATE APPLICATION ROLE では確認されます。  
  
 パラメーター*パスワード*一方向のハッシュとして格納されます。  
  
 **Sp_addapprole**ストアド プロシージャは、ユーザー定義のトランザクション内から実行することはできません。  
  
> [!IMPORTANT]  
>  Microsoft ODBC**暗号化**では、オプションはサポートされていない**SqlClient**です。 可能な場合は、アプリケーション ロールの資格情報の入力を求めるメッセージを実行時に表示してください。 資格情報をファイルに保存するのは避けてください。 資格情報を保持する必要がある場合は、CryptoAPI 関数を使用して暗号化します。  
  
## <a name="permissions"></a>権限  
 データベースに対する ALTER ANY APPLICATION ROLE 権限が必要です。 新しいロールと同じ名前および同じ所有者のスキーマが存在しない場合は、そのデータベースに対する CREATE SCHEMA 権限も必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、新しいアプリケーション ロールを追加`SalesApp`パスワードを使用して`x97898jLJfcooFUYLKm387gf3`現在のデータベースにします。  
  
```  
EXEC sp_addapprole 'SalesApp', 'x97898jLJfcooFUYLKm387gf3' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md)  
  
  
