---
title: "(TRANSACT-SQL) の証明書を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CERTIFICATE
- CREATE_CERTIFICATE_TSQL
- sql13.swb.createcertificate.f1
- CERTIFICATE_TSQL
- CREATE CERTIFICATE
- sql13.swb.certificateproperties.f1
dev_langs: TSQL
helpviewer_keywords:
- encryption [SQL Server], certificates
- certificates [SQL Server], adding
- certificates [SQL Server]
- adding certificates
- cryptography [SQL Server], certificates
- CREATE CERTIFICATE statement
ms.assetid: a4274b2b-4cb0-446a-a956-1c8e6587515d
caps.latest.revision: "74"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b77ff590d36f866c8679bfbc16e605565d9d8d1d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="create-certificate-transact-sql"></a>CREATE CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベースに証明書を追加する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 この機能は、データ層アプリケーション フレームワーク (DACFx) を使用してデータベースのエクスポートとの互換性はありません。 エクスポートする前に、すべての証明書を削除する必要があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
CREATE CERTIFICATE certificate_name [ AUTHORIZATION user_name ]   
    { FROM <existing_keys> | <generate_new_keys> }  
    [ ACTIVE FOR BEGIN_DIALOG =  { ON | OFF } ]  
  
<existing_keys> ::=   
    ASSEMBLY assembly_name  
    | {   
        [ EXECUTABLE ] FILE = 'path_to_file'  
        [ WITH PRIVATE KEY ( <private_key_options> ) ]   
      }  
    | {   
        BINARY = asn_encoded_certificate  
        [ WITH PRIVATE KEY ( <private_key_options> ) ]  
      }  
<generate_new_keys> ::=   
    [ ENCRYPTION BY PASSWORD = 'password' ]   
    WITH SUBJECT = 'certificate_subject_name'   
    [ , <date_options> [ ,...n ] ]   
  
<private_key_options> ::=  
      {   
        FILE = 'path_to_private_key'  
         [ , DECRYPTION BY PASSWORD = 'password' ]  
         [ , ENCRYPTION BY PASSWORD = 'password' ]    
      }  
    |  
      {   
        BINARY = private_key_bits  
         [ , DECRYPTION BY PASSWORD = 'password' ]  
         [ , ENCRYPTION BY PASSWORD = 'password' ]    
      }  
  
<date_options> ::=  
    START_DATE = 'datetime' | EXPIRY_DATE = 'datetime'  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CREATE CERTIFICATE certificate_name   
    { <generate_new_keys> | FROM <existing_keys> }  
    [ ; ]  
  
<generate_new_keys> ::=   
    WITH SUBJECT ='certificate_subject_name'   
    [ , <date_options> [ ,...n ] ]   
  
<existing_keys> ::=   
    {   
      FILE ='path_to_file'  
      WITH PRIVATE KEY   
         (   
           FILE ='path_to_private_key'  
           , DECRYPTION BY PASSWORD ='password'   
         )  
    }  
  
<date_options> ::=  
    START_DATE ='datetime' | EXPIRY_DATE ='datetime'  
```  
  
## <a name="arguments"></a>引数  
 *certificate_name*  
 データベース内の証明書の名前です。  
  
 承認*user_name*  
 この証明書を所有するユーザーの名前です。  
  
 アセンブリ*アセンブリ名*  
 データベース内に既に読み込まれている署名付きアセンブリを指定します。  
  
 [実行可能ファイル]ファイル ='*path_to_file*'  
 証明書が含まれる DER エンコード ファイルへの完全なパスを、ファイル名を含めて指定します。 EXECUTABLE オプションを使用する場合、ファイルはこの証明書によって署名された DLL になります。 *path_to_file*ローカル パスまたはネットワーク上の場所への UNC パスを指定できます。 ファイルのアクセスのセキュリティ コンテキストで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウント。 このアカウントは、ファイル システムで必要となる権限を保持している必要があります。  
  
 WITH PRIVATE KEY  
 証明書の秘密キーが読み込まれることを示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 この句は、ファイルから証明書を作成する場合にのみ有効です。 アセンブリの秘密キーを読み込むには、次のように使用します。 [ALTER CERTIFICATE](../../t-sql/statements/alter-certificate-transact-sql.md)です。  
  
 ファイル ='*path_to_private_key*'  
 秘密キーへの完全なパスを、ファイル名を含めて指定します。 *path_to_private_key*ローカル パスまたはネットワーク上の場所への UNC パスを指定できます。 ファイルのアクセスのセキュリティ コンテキストで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウント。 このアカウントに必要なファイル システム権限が必要です。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
 asn_encoded_certificate  
 バイナリ定数として指定された、ASN でエンコードされた証明書ビット。  
  
 バイナリ =*private_key_bits*  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 バイナリ定数として指定された秘密キーのビット。 これらのビットは暗号化された形式でもかまいません。 暗号化されている場合は、ユーザーは暗号化解除パスワードを指定する必要があります。 パスワード ポリシーのチェックは、このパスワードに対しては実行されません。 秘密キーのビットは PVK ファイル形式にする必要があります。  
  
 DECRYPTION BY PASSWORD ='*key_password*'  
 ファイルから取得する秘密キーの暗号化解除に必要なパスワードを指定します。 秘密キーが NULL パスワードで保護されている場合、この句は省略可能です。 パスワード保護なしで秘密キーをファイルに保存することは推奨されません。 パスワードが必要ですが、パスワードが指定されていない、ステートメントは失敗します。  
  
 ENCRYPTION BY PASSWORD ='*パスワード*'  
 秘密キーの暗号化に使用するパスワードを指定します。 このオプションは、証明書をパスワードで暗号化する場合にのみ使用します。 この句を省略すると、データベース マスター _ キーを使用して、秘密キーが暗号化されます。 *パスワード*のインスタンスを実行しているコンピューターの Windows パスワード ポリシーの要件を満たす必要がある[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 詳細については、「 [Password Policy](../../relational-databases/security/password-policy.md)」をご参照ください。  
  
 サブジェクト ='*certificate_subject_name*'  
 用語*サブジェクト*X.509 標準で定義されている証明書のメタデータでフィールドを参照します。 サブジェクトが 64 文字にする必要があり、に対してはこの制限は適用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Linux にします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows では、サブジェクトは最大 128 文字を使用できます。 128 文字以下の項目には、カタログに格納されますが、バイナリ ラージ オブジェクト (BLOB)、証明書を含む完全なサブジェクト名を保持する場合は切り捨てられます。  
  
 START_DATE ='*datetime*'  
 証明書が有効となる日付を指定します。 指定しない場合、START_DATE は現在の日付に等しいに設定されます。 START_DATE は UTC 時刻で、日時に変換可能な任意の形式で指定できます。  
  
 EXPIRY_DATE ='*datetime*'  
 証明書が期限切れとなる日付を指定します。 指定しない場合、EXPIRY_DATE は START_DATE の後に 1 つの年の日付に設定されます。 EXPIRY_DATE は UTC 時刻で、日時に変換可能な任意の形式で指定できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Service Broker では、有効期限の日付を確認します。 ただし、暗号化、証明書を使用する場合、有効期限は適用されません。  
  
 ACTIVE FOR BEGIN_DIALOG = { **ON** |オフ}  
 発信側に証明書を使用できるように、[!INCLUDE[ssSB](../../includes/sssb-md.md)]ダイアログ メッセージ交換します。 既定値は ON です。  
  
## <a name="remarks"></a>解説  
 証明書は、X.509 標準に準拠したデータベース レベルのセキュリティ保護可能なリソースであり、X.509 V1 フィールドをサポートします。 CREATE CERTIFICATE では、ファイルまたはアセンブリから証明書を読み込むことができます。 このステートメントでは、キー ペアを生成して自己署名証明書を作成することもできます。  
  
 秘密キーである必要があります\<= 暗号化された形式で 2500 バイトです。 によって生成された秘密キー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は 1024 ビットまでの時間[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]2048 ビット長はで始まり、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。 外部ソースからインポートされる秘密キーの最小の長さは 384 ビットで、最大の長さは 4,096 ビットです。 インポートされる秘密キーの長さは、64 ビットの整数倍であることが必要です。 TDE に使用される証明書では、秘密キーのサイズが 3456 ビットに制限されています。  
  
 証明書の全体のシリアル番号が格納されているが、sys.certificates カタログ ビューで最初の 16 バイトのみが表示されます。  
  
 証明書の発行者フィールド全体が格納されているが、カタログ ビューの sys.certificates で最初の 884 バイトのみです。  
  
 秘密キーがで指定されたパブリック キーに対応する必要があります*certificate_name*です。  
  
 証明書をコンテナーから作成する場合、秘密キーの読み込みは省略可能です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]自己署名入りの証明書を生成、秘密キーは常に作成します。 既定では、秘密キーはデータベースのマスター キーを使用して暗号化されます。 データベース マスター _ キーが存在しないため、パスワードが指定されていない、ステートメントは失敗します。  
  
 ENCRYPTION BY PASSWORD オプションは、秘密キーは、データベース マスター _ キーで暗号化されている場合は必要ありません。 秘密キーがパスワードで暗号化された場合にのみ、このオプションを使用します。 パスワードを指定しない場合、証明書の秘密キーは、データベースのマスター キーを使用して暗号化されます。 データベースのマスター_キーを開くことができない、この句を省略すると、エラーが発生します。  
  
 秘密キーがデータベース マスター キーを使って暗号化されている場合は、暗号化解除のパスワードを指定する必要はありません。  
  
> [!NOTE]  
>  暗号化や署名用の組み込み関数では、証明書の有効期限はチェックされません。 これらの関数を使用する場合、ユーザーは、証明書の有効期限をいつチェックするかを自分で決定する必要があります。  
  
 使用して、証明書のバイナリ記述を作成することができます、 [CERTENCODED (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/certencoded-transact-sql.md)と[CERTPRIVATEKEY (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/certprivatekey-transact-sql.md)関数。 使用する例については**CERTPRIVATEKEY**と**CERTENCODED**証明書を別のデータベースにコピーするには、例 B のトピックを参照してください。 [CERTENCODED (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/certencoded-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 データベースに対する CREATE CERTIFICATE 権限が必要です。 Windows のログインのみに使用する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン、およびアプリケーション ロールは、証明書を所有できます。 グループとロールは証明書を所有できません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-self-signed-certificate"></a>A. 自己署名証明書を作成する  
 次の例と呼ばれる証明書を作成する`Shipping04`です。 この証明書の秘密キーは、パスワードを使用して保護されます。  
  
```  
CREATE CERTIFICATE Shipping04   
   ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y'  
   WITH SUBJECT = 'Sammamish Shipping Records',   
   EXPIRY_DATE = '20201031';  
GO  
```  
  
### <a name="b-creating-a-certificate-from-a-file"></a>B. ファイルから証明書を作成する  
 次の例では、データベースに証明書を作成し、ファイルからキー ペアを読み込みます。  
  
```  
CREATE CERTIFICATE Shipping11   
    FROM FILE = 'c:\Shipping\Certs\Shipping11.cer'   
    WITH PRIVATE KEY (FILE = 'c:\Shipping\Certs\Shipping11.pvk',   
    DECRYPTION BY PASSWORD = 'sldkflk34et6gs%53#v00');  
GO   
```  
  
### <a name="c-creating-a-certificate-from-a-signed-executable-file"></a>C. 署名付き実行可能ファイルから証明書を作成する  
  
```  
CREATE CERTIFICATE Shipping19   
    FROM EXECUTABLE FILE = 'c:\Shipping\Certs\Shipping19.dll';  
GO  
```  
  
 またはからアセンブリを作成することができます、`dll`ファイル、およびアセンブリから証明書を作成します。  
  
```  
CREATE ASSEMBLY Shipping19   
    FROM ' c:\Shipping\Certs\Shipping19.dll'   
    WITH PERMISSION_SET = SAFE;  
GO  
CREATE CERTIFICATE Shipping19 FROM ASSEMBLY Shipping19;  
GO  
```  
  
### <a name="d-creating-a-self-signed-certificate"></a>D. 自己署名証明書を作成する  
 次の例と呼ばれる証明書を作成する`Shipping04`暗号化パスワードを指定することがなくです。 この例で使用できる[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。
  
```  
CREATE CERTIFICATE Shipping04   
   WITH SUBJECT = 'Sammamish Shipping Records';  
GO  
```  
  
  
## <a name="see-also"></a>参照  
 [ALTER CERTIFICATE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [証明書 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [CERTENCODED &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/certencoded-transact-sql.md)   
 [CERTPRIVATEKEY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/certprivatekey-transact-sql.md)  
  
  


