---
title: sp_describe_parameter_encryption (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 07/27/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_describe_parameter_encryption
- sp_describe_parameter_encryption_TSQL
- sys.sp_describe_parameter_encryption
- sys.sp_describe_parameter_encryption_TSQL
helpviewer_keywords:
- sp_describe_parameter_encryption
ms.assetid: 706ed441-2881-4934-8d5e-fb357ee067ce
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 377a1e342970e9593b37924c3739ee7a706d5264
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053033"
---
# <a name="spdescribeparameterencryption-transact-sql"></a>sp_describe_parameter_encryption (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  指定された分析[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントとパラメーターは、パラメーターは、Always Encrypted 機能を使用して保護されているデータベース列に対応を判断します。 暗号化された列に対応するパラメーターの暗号化メタデータを返します。  
  
## <a name="syntax"></a>構文  
  
```  
sp_describe_parameter_encryption   
    [ @tsql = ] N'Transact-SQL_batch' ,   
    [ @params = ] N'parameters'   
[ ;]  
```  
  
## <a name="arguments"></a>引数  
 [ \@tsql =] ' Transact SQL_batch'  
 1 つ以上の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントです。 Nvarchar (n) または nvarchar (max)、transact SQL_batch 可能性があります。  
  
 [ \@params =] 'N'parameters  
 *\@params* TRANSACT-SQL バッチには、sp_executesql と同様に、パラメーターの宣言文字列を提供します。 パラメーターには、nvarchar (n) または nvarchar (max) があります。  
  
 1 つの文字列に埋め込まれたすべてのパラメーターの定義を含む、 [!INCLUDE[tsql](../../includes/tsql-md.md)]_batch します。 この文字列は Unicode 定数または Unicode 変数にする必要があります。 各パラメーター定義は、パラメーター名とデータ型で構成されます。 *n*は追加のパラメーター定義を示すプレース ホルダーです。 ステートメントで指定されたすべてのパラメーターを定義する必要があります *\@params*します。 場合、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはステートメント内のバッチは、パラメーターを含まない *\@params*は必要ありません。 NULL は、このパラメーターの既定値です。  
  
## <a name="return-value"></a>戻り値  
 0 は成功を示します。 その他は、エラーを示します。  
  
## <a name="result-sets"></a>結果セット  
 **sp_describe_parameter_encryption** 2 つの結果セットが返されます。  
  
-   結果セットは、データベース列の指定したパラメーター用に構成された暗号化キーを記述する[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントに対応しています。  
  
-   結果セットをどのように特定のパラメーターの記述を暗号化する必要があります。 この結果は、最初の結果セットで説明するキーの参照を設定します。  
  
 最初の結果セットの各行には、キーのペアがについて説明します暗号化された列暗号化キーとその対応する列のマスター _ キー。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**column_encryption_key_ordinal**|**int**|結果セットの行の id。|  
|**database_id**|**int**|データベース id。|  
|**column_encryption_key_id**|**int**|列暗号化キーの id。注: この id は内の行を表します、 [sys.column_encryption_keys &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)カタログ ビューです。|  
|**column_encryption_key_version**|**int**|将来使用するために予約されています。 現時点では、1 を常に含まれています。|  
|**column_encryption_key_metadata_version**|**binary(8)**|列暗号化キーの作成時刻を表すタイムスタンプです。|  
|**column_encryption_key_encrypted_value**|**varbinary(4000)**|列暗号化キーの暗号化された値。|  
|**column_master_key_store_provider_name**|**sysname**|列暗号化キーの暗号化された値を生成するために使用された列マスター_キーを含むキー ストア プロバイダーの名前。|  
|**column_master_key_path**|**nvarchar (4000)**|列暗号化キーの暗号化された値を生成するために使用された列マスター_キーのキーのパス。|  
|**column_encryption_key_encryption_algorithm_name**|**sysname**|列暗号化キーの暗号化値を生成するために使用される暗号化アルゴリズムの名前。|  
  
 2 つ目の結果セットの各行には、1 つのパラメーターの暗号化メタデータが含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**parameter_ordinal**|**int**|結果セット内の行の id。|  
|**parameter_name**|**sysname**|指定されたパラメーターのいずれかの名前、  *\@params*引数。|  
|**column_encryption_algorithm**|**tinyint**|パラメーターの列に対して構成されている暗号化アルゴリズムを示すコードに対応します。 現在サポートされている値は次のとおりです。2 **AEAD_AES_256_CBC_HMAC_SHA_256**します。|  
|**column_encryption_type**|**tinyint**|パラメーターの列に対して構成されている暗号化の種類を示すコードに対応します。 サポートされている値は次のとおりです。<br /><br /> 0 - プレーン テキスト (列は暗号化されません)<br /><br /> 1-ランダム化された暗号化<br /><br /> 2-決定論的暗号化します。|  
|**column_encryption_key_ordinal**|**int**|最初の結果内の行のコードを設定します。 参照先の行、列に対して構成された列暗号化キーの説明、パラメーターに対応しています。|  
|**column_encryption_normalization_rule_version**|**tinyint**|型の正規化アルゴリズムのバージョン番号。|  
  
## <a name="remarks"></a>コメント  
 A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、Always Encrypted をサポートしているクライアント ドライバーが自動的に呼び出します**sp_describe_parameter_encryption**パラメーター化されたクエリでは、アプリケーションによって発行された暗号化メタデータを取得します。 その後、ドライバーは暗号化メタデータを使用して Always Encrypted で保護されたデータベース列に対応するパラメーターの値を暗号化し、プレーン テキストの暗号化された使用して、アプリケーションによって送信されたパラメーター値に置換されます。データベース エンジンにクエリを送信する前に、パラメーターの値  
  
## <a name="permissions"></a>アクセス許可  
 必要な**VIEW ANY COLUMN ENCRYPTION KEY DEFINITION**と**VIEW ANY COLUMN MASTER KEY DEFINITION**データベースのアクセス許可。  
  
## <a name="examples"></a>使用例  
  
```  
CREATE COLUMN MASTER KEY [CMK1]  
WITH  
(  
       KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',  
    KEY_PATH = N'CurrentUser/my/A66BB0F6DD70BDFF02B62D0F87E340288E6F9305'  
);  
GO  
  
CREATE COLUMN ENCRYPTION KEY [CEK1]  
WITH VALUES  
(  
       COLUMN_MASTER_KEY = [CMK1],  
    ALGORITHM = 'RSA_OAEP',  
    ENCRYPTED_VALUE =   
0x016E000001630075007200720065006E00740075007300650072002F006D007  
9002F00610036003600620062003000660036006400640037003000620064006  
6006600300032006200360032006400300066003800370065003300340030003  
200380038006500360066003900330030003500CA0D0CEC74ECADD1804CF991  
37B4BD06BBAB15D7EA74E0C249A779C7768A5B659E0125D24FF827F5EA8CA51  
7A8E197ECA1353BA814C2B0B2E6C8AB36E3AE6A1E972D69C3C573A963ADAB6  
686CF5D24F95FE43140C4F9AF48FBA7DF2D053F3B4A1F5693A1F905440F8015B  
DB43AF8A04BE4E045B89876A0097E5FBC4E6A3B9C3C0D278C540E46C53938B8  
C957B689C4DC095821C465C73117CBA95B758232F9E5B2FCC7950B8CA00AFE3  
74DE42847E3FBC2FDD277035A2DEF529F4B735C20D980073B4965B4542A3472  
3276A1646998FC6E1C40A3FDB6ABCA98EE2B447F114D2AC7FF8C7D51657550E  
C5C2BABFFE8429B851272086DCED94332CF18FA854C1D545A28B1EF4BE64F8E0  
35175C1650F6FC5C4702ACF99850A4542B3747EAEC0CC726E091B36CE24392D8  
01ECAA684DE344FECE05812D12CD72254A014D42D0EABDA41C89FC4F545E88B  
4B8781E5FAF40D7199D4842D2BFE904D209728ED4F527CBC169E2904F6E711FF8  
1A8F4C25382A2E778DD2A58552ED031AFFDA9D9D891D98AD82155F93C58202F  
C24A77F415D4F8EF22419D62E188AC609330CCBD97CEE1AEF8A18B0195883360  
4707FDF03B2B386487CC679D7E352D0B69F9FB002E51BCD814D077E82A09C14E  
9892C1F8E0C559CFD5FA841CEF647DAB03C8191DC46B772E94D579D8C80FE93C  
3827C9F0AE04D5325BC73111E07EEEDBE67F1E2A73580085  
);  
GO  
  
CREATE TABLE t1 (  
c1 INT ENCRYPTED WITH (  
    COLUMN_ENCRYPTION_KEY = [CEK_Auto1],   
    ENCRYPTION_TYPE = Randomized,   
    ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NULL,  
);  
  
EXEC sp_describe_parameter_encryption N'INSERT INTO t1 VALUES(@c1)',  N'@c1 INT';  
```  
  
 最初の結果セットを次に示します。  
  
|column_encryption_key_ordinal|database_id|column_encryption_key_id|column_encryption_key_version|column_encryption_key_metadata_version|column_encryption_key_encrypted_value|  
|--------------------------------------|------------------|---------------------------------|--------------------------------------|------------------------------------------------|-----------------------------------------------|  
|1|5|1|1|0x99EDA60083A50000|0x016E000001630075007200720065006E00740075007300650072002F006D0079002F006100360036006200620030006600360064006400370030006200640066006600300032006200360032006400300066003800370065003300340030003200380038006500360066003900330030003500CA0D0CEC74ECADD1804CF99137B4BD06BBAB15D7EA74E0C249A779C7768A5B659E0125D24FF827F5EA8CA517A8E197ECA1353BA814C2B0B2E6C8AB36E3AE6A1E972D69C3C573A963ADAB6686CF5D24F95FE43140C4F9AF48FBA7DF2D053F3B4A1F5693A1F905440F8015BDB43AF8A04BE4E045B89876A0097E5FBC4E6A3B9C3C0D278C540E46C53938B8C957B689C4DC095821C465C73117CBA95B758232F9E5B2FCC7950B8CA00AFE374DE42847E3FBC2FDD277035A2DEF529F4B735C20D980073B4965B4542A34723276A1646998FC6E1C40A3FDB6ABCA98EE2B447F114D2AC7FF8C7D51657550EC5C2BABFFE8429B851272086DCED94332CF18FA854C1D545A28B1EF4BE64F8E035175C1650F6FC5C4702ACF99850A4542B3747EAEC0CC726E091B36CE24392D801ECAA684DE344FECE05812D12CD72254A014D42D0EABDA41C89FC4F545E88B4B8781E5FAF40D7199D4842D2BFE904D209728ED4F527CBC169E2904F6E711FF81A8F4C25382A2E778DD2A58552ED031AFFDA9D9D891D98AD82155F93C58202FC24A77F415D4F8EF22419D62E188AC609330CCBD97CEE1AEF8A18B01958833604707FDF03B2B386487CC679D7E352D0B69F9FB002E51BCD814D077E82A09C14E9892C1F8E0C559CFD5FA841CEF647DAB03C8191DC46B772E94D579D8C80FE93C3827C9F0AE04D5325BC73111E07EEEDBE67F1E2A73580085|  
  
 (結果を続行します。)  
  
|column_master_key_store_provider_name|column_master_key_path|column_encryption_key_encryption_algorithm_name|  
|------------------------------------------------|-------------------------------|----------------------------------------------------------|  
|MSSQL_CERTIFICATE_STORE|CurrentUser/マイ/A66BB0F6DD70BDFF02B62D0F87E340288E6F9305|RSA_OAEP|  
  
 2 つ目の結果セットを次に示します。  
  
|parameter_ordinal|parameter_name|column_encryption_algorithm|column_encryption_type|  
|------------------------|---------------------|-----------------------------------|------------------------------|  
|1|\@c1|1|1|  
  
 (結果を続行します。)  
  
|column_encryption_key_ordinal|column_encryption_normalization_rule_version|  
|--------------------------------------|------------------------------------------------------|  
|1|1|  
  
## <a name="see-also"></a>関連項目  
 [Always Encrypted &#40;データベース エンジン&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [Always Encrypted &#40;クライアント開発&#41;](../../relational-databases/security/encryption/always-encrypted-client-development.md)  
  
  
