---
title: "ALTER ENDPOINT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- ALTER ENDPOINT
- ALTER_ENDPOINT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER ENDPOINT statement
- modifying endpoints
- endpoints [SQL Server], modifying
ms.assetid: 70f35566-30cf-47c6-8394-dfe5d71629d3
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f33dfa3c49397a5f69a59420b74e3cfdeae25857
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="alter-endpoint-transact-sql"></a>ALTER ENDPOINT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  既存のエンドポイントを、次の方法で変更できるようにします。  
  
-   新しいメソッドを既存のエンドポイントに追加する。  
  
-   既存のメソッドを変更するか、またはエンドポイントから削除する。  
  
-   エンドポイントのプロパティを変更する。  
  
> [!NOTE]  
>  このトピックでは、ALTER ENDPOINT に固有の構文および引数について説明します。 CREATE ENDPOINT と ALTER ENDPOINT の両方に共通する引数の説明については、次を参照してください。 [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md).  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] からは、ネイティブ XML Web サービス (SOAP/HTTP エンドポイント) は削除されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER ENDPOINT endPointName [ AUTHORIZATION login ]  
[ STATE = { STARTED | STOPPED | DISABLED } ]  
[ AS { TCP } ( <protocol_specific_items> ) ]  
[ FOR { TSQL | SERVICE_BROKER | DATABASE_MIRRORING } (  
   <language_specific_items>  
        ) ]  
  
<AS TCP_protocol_specific_arguments> ::=  
AS TCP (  
  LISTENER_PORT = listenerPort  
  [ [ , ] LISTENER_IP = ALL | ( 4-part-ip ) | ( "ip_address_v6" ) ]  
)  
<FOR SERVICE_BROKER_language_specific_arguments> ::=  
FOR SERVICE_BROKER (  
   [ AUTHENTICATION = {   
      WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]  
      | CERTIFICATE certificate_name   
      | WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ] CERTIFICATE certificate_name   
      | CERTIFICATE certificate_name WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]   
    } ]  
   [ , ENCRYPTION = { DISABLED   
       |   
         {{SUPPORTED | REQUIRED }   
       [ ALGORITHM { RC4 | AES | AES RC4 | RC4 AES } ] }   
   ]  
  
  [ , MESSAGE_FORWARDING = {ENABLED | DISABLED} ]  
  [ , MESSAGE_FORWARD_SIZE = forwardSize  
)  
  
<FOR DATABASE_MIRRORING_language_specific_arguments> ::=  
FOR DATABASE_MIRRORING (  
   [ AUTHENTICATION = {   
      WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]  
      | CERTIFICATE certificate_name   
      | WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ] CERTIFICATE certificate_name   
      | CERTIFICATE certificate_name WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]   
    } ]  
   [ , ENCRYPTION = { DISABLED   
       |   
         {{SUPPORTED | REQUIRED }   
       [ ALGORITHM { RC4 | AES | AES RC4 | RC4 AES } ] }   
    ]   
   [ , ] ROLE = { WITNESS | PARTNER | ALL }  
)  
  
```  
  
## <a name="arguments"></a>引数  
  
> [!NOTE]  
>  次の引数は、ALTER ENDPOINT に固有の引数です。 残りの引数の詳細については、次を参照してください。 [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md).  
  
 **AS** { **TCP** }  
 トランスポート プロトコルを変更することはできません**ALTER ENDPOINT**です。  
  
 **AUTHORIZATION** *login*  
 **承認**オプションでは使用できません**ALTER ENDPOINT**です。 エンドポイントの作成時にのみ所有者を割り当てることができます。  
  
 **FOR** { **TSQL** | **SERVICE_BROKER** | **DATABASE_MIRRORING** }  
 ペイロードの種類を変更することはできません**ALTER ENDPOINT**です。  
  
## <a name="remarks"></a>解説  
 ALTER ENDPOINT を使用する場合、更新するパラメーターのみを指定します。 既存のエンドポイントのすべてのプロパティは、明示的に変更しない限り変更されません。  
  
 ENDPOINT DDL ステートメントは、ユーザー トランザクション内部では実行できません。  
  
 エンドポイントで使用する暗号化アルゴリズムの選択方法の詳細については、次を参照してください。 [Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)です。  
  
> [!NOTE]  
>  RC4 アルゴリズムは、旧バージョンとの互換性のためにのみサポートされています。 データベース互換性レベルが 90 または 100 の場合、新しい素材は RC4 または RC4_128 を使用してのみ暗号化できます  (非推奨)。AES アルゴリズムのいずれかなど、新しいアルゴリズムを使用してください。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]でき、以降のバージョンでは、RC4 または RC4_128 を使用して暗号化された素材を暗号化が解除されたどの互換性レベルです。  
>   
>  RC4 は比較的弱いアルゴリズムで、AES は比較的強いアルゴリズムです。 しかし、AES は RC4 に比べて非常に処理が遅くなります。 速度よりもセキュリティを優先する場合は、AES を使用することをお勧めします。  
  
## <a name="permissions"></a>権限  
 ユーザーのメンバーである必要があります、 **sysadmin**固定サーバー ロール、エンドポイントの所有者または ALTER ANY ENDPOINT 権限が与えられています。  
  
 既存のエンドポイントの所有権を変更するには、ALTER AUTHORIZATION ステートメントを使用する必要があります。 詳細については、次を参照してください。 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
 詳細については、「 [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [DROP ENDPOINT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-endpoint-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
