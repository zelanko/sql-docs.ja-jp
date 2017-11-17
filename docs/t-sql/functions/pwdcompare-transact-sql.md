---
title: "PWDCOMPARE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PWDCOMPARE
- PWDCOMPARE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sa account
- passwords [SQL Server], blank
- PWDCOMPARE function [Transact-SQL]
ms.assetid: 5f84ff9e-c1ec-46aa-8501-50f854ebcc3a
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6aadde33d6d1ee1404170197c32ab77ade2dbfad
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="pwdcompare-transact-sql"></a>PWDCOMPARE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パスワードをハッシュして既存のパスワードのハッシュと比較します。 PWDCOMPARE は空白の検索に使用できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン パスワードや、よくある脆弱なパスワード。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
PWDCOMPARE ( 'clear_text_password'  
   , password_hash   
   [ , version ] )  
```  
  
## <a name="arguments"></a>引数  
 **'** *clear_text_password* **'**  
 暗号化されていないパスワードです。 *clear_text_password*は**sysname** (**nvarchar (128)**)。  
  
 *password_hash*  
 パスワードの暗号化ハッシュです。 *password_hash*は**varbinary (128)**です。  
  
 *バージョン*  
 場合は、1 に設定することができるパラメーターを廃止*password_hash*ログインから値を表すよりも前[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]に移行する[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降に変換されていないのか、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]システム。 *バージョン*は**int**です。  
  
> [!CAUTION]  
>  このパラメーターは、旧バージョンと互換性のため、の提供されますが、パスワード ハッシュ blob にはここで、独自のバージョンの説明が含まれているために無視されます。 [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
 場合 1 を返しますのハッシュ、 *clear_text_password*と一致する、 *password_hash*パラメーターとそうでない場合は 0 です。  
  
## <a name="remarks"></a>解説  
 PWDCOMPARE 関数は、パスワード ハッシュの強度に対する脅威にはなりません。このテストは、最初のパラメーターとして渡されるパスワードを使用してログインしようとした場合に実行されるテストと同じテストです。  
  
 **PWDCOMPARE**包含データベース ユーザーのパスワードを使用することはできません。 該当する包含データベースは存在しません。  
  
## <a name="permissions"></a>Permissions  
 PWDENCRYPT は、パブリックで使用できます。  
  
 sys.sql_logins の password_hash 列を調べるには CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-identifying-logins-that-have-no-passwords"></a>A. パスワードがないログインを特定する  
 次の例では、パスワードがない [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを特定します。  
  
```  
SELECT name FROM sys.sql_logins   
WHERE PWDCOMPARE('', password_hash) = 1 ;  
```  
  
### <a name="b-searching-for-common-passwords"></a>B. よくあるパスワードを検索する  
 よくあるパスワードを見つけて変更できるように検索するには、そのパスワードを最初のパラメーターとして指定します。 たとえば、として指定されたパスワードを検索する次のステートメントを実行`password`です。  
  
```  
SELECT name FROM sys.sql_logins   
WHERE PWDCOMPARE('password', password_hash) = 1 ;  
```  
  
## <a name="see-also"></a>参照  
 [PWDENCRYPT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/pwdencrypt-transact-sql.md)   
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  

