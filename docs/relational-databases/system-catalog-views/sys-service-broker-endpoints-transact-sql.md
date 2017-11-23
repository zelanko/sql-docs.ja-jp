---
title: "sys.service_broker_endpoints (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.service_broker_endpoints_TSQL
- service_broker_endpoints
- service_broker_endpoints_TSQL
- sys.service_broker_endpoints
dev_langs: TSQL
helpviewer_keywords: sys.service_broker_endpoints catalog view
ms.assetid: 6979ec9b-0043-411e-aafb-0226fa26c5ba
caps.latest.revision: "51"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d7f9fdc08d74c9ca3e8c469462451fdd7bc5e49b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysservicebrokerendpoints-transact-sql"></a>sys.service_broker_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このカタログ ビューには Service Broker エンドポイントごとに 1 行のデータが格納されます。 このビューの各行は、同じ行に対応**endpoint_id**で、 **sys.tcp_endpoints** TCP 構成メタデータを含むビュー。 Service Broker で使用できるプロトコルは TCP のみです。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<継承された列 >**|**--**|列を継承[sys.endpoints &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**is_message_forwarding_enabled**|**bit**|エンドポイントのサポート メッセージを転送します。 初期設定は**0** (無効)。 Null を許容しません。|  
|**message_forwarding_size**|**int**|最大のメガバイト数**tempdb**メッセージの転送に使用する領域が許可されています。 初期設定は**10**です。 Null を許容しません。|  
|**connection_auth**|**tinyint**|エンドポイントへの接続に必要な接続認証の種類。次のいずれかになります。<br /><br /> **1** -NTLM<br /><br /> **2** -KERBEROS<br /><br /> **3** -NEGOTIATE<br /><br /> **4** -証明書<br /><br /> **5** -NTLM、CERTIFICATE<br /><br /> **6** -KERBEROS、CERTIFICATE<br /><br /> **7** -NEGOTIATE、CERTIFICATE<br /><br /> **8** -CERTIFICATE、NTLM<br /><br /> **9** -証明書、KERBEROS<br /><br /> **10** -CERTIFICATE、NEGOTIATE<br /><br /> Null を許容しません。|  
|**connection_auth_desc**|**nvarchar (60)**|エンドポイントへの接続に必要な接続認証の種類の説明。次のいずれかになります。<br /><br /> NTLM<br /><br /> KERBEROS<br /><br /> NEGOTIATE<br /><br /> CERTIFICATE<br /><br /> NTLM、CERTIFICATE<br /><br /> KERBEROS、CERTIFICATE<br /><br /> NEGOTIATE、CERTIFICATE<br /><br /> CERTIFICATE、NTLM<br /><br /> CERTIFICATE、KERBEROS<br /><br /> CERTIFICATE、NEGOTIATE<br /><br /> NULL 値は許可されます。|  
|**certificate_id**|**int**|認証で使用される証明書の ID (存在する場合)。<br /><br /> 0 = Windows 認証が使用されます。|  
|**encryption_algorithm**|**tinyint**|暗号化アルゴリズムです。 説明および対応する DDL オプションと共に使用できる値を次に示します。<br /><br /> **0** : なし。 対応する DDL オプション: 無効になっています。<br /><br /> **1** : RC4 です。 対応する DDL オプション: {が必要 (& m); #124アルゴリズム RC4 が必要}。<br /><br /> **2** : AES です。 対応する DDL オプション: アルゴリズム AES が必要です。<br /><br /> **3** : NONE、RC4 です。 対応する DDL オプション: {サポートされている (&) #124 です。アルゴリズム RC4 をサポート}。<br /><br /> **4** : NONE、AES です。 対応する DDL オプション: アルゴリズム AES をサポートします。<br /><br /> **5** : RC4、AES です。 対応する DDL オプション: アルゴリズム RC4 AES が必要です。<br /><br /> **6** : AES、RC4 です。 対応する DDL オプション: アルゴリズム AES RC4 が必要です。<br /><br /> **7** : NONE、RC4、AES です。 対応する DDL オプション: アルゴリズム RC4 AES をサポートします。<br /><br /> **8** : NONE、AES、RC4 です。 対応する DDL オプション: アルゴリズム AES RC4 をサポートします。<br /><br /> Null を許容しません。|  
|**encryption_algorithm_desc**|**nvarchar (60)**|暗号化アルゴリズムの説明。 使用可能な値と、対応する DDL オプションは、次に示します。<br /><br /> NONE: 無効になっています。<br /><br /> RC4: {が必要 (& m); #124必須のアルゴリズム RC4}<br /><br /> アルゴリズム AES が必要: AES<br /><br /> NONE、RC4: {サポート &#124;です。アルゴリズム RC4 をサポート}<br /><br /> NONE、AES: サポートされているアルゴリズム AES<br /><br /> RC4、AES: 必須のアルゴリズム RC4 AES<br /><br /> AES、RC4: 必須のアルゴリズム AES RC4<br /><br /> : NONE、RC4、AES アルゴリズム RC4 をサポートする AES<br /><br /> : NONE、AES、RC4 アルゴリズム AES RC4 をサポートします。<br /><br /> NULL 値は許可されます。|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]  
>  RC4 アルゴリズムは、旧バージョンとの互換性のためにのみサポートされています。 データベース互換性レベルが 90 または 100 の場合、新しい素材は RC4 または RC4_128 を使用してのみ暗号化できます  (非推奨)。AES アルゴリズムのいずれかなど、新しいアルゴリズムを使用してください。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]でき、以降のバージョンでは、RC4 または RC4_128 を使用して暗号化された素材を暗号化が解除されたどの互換性レベルです。  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ALTER ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-endpoint-transact-sql.md)   
 [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md)  
  
  
