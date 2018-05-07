---
title: sys.database_mirroring_endpoints (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.database_mirroring_endpoints_TSQL
- database_mirroring_endpoints
- sys.database_mirroring_endpoints
- database_mirroring_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], endpoint
- HADR [SQL Server], endpoint
- database mirroring [SQL Server], catalog views
- sys.database_mirroring_endpoints catalog view
ms.assetid: f2285199-97ad-473c-a52d-270044dd862b
caps.latest.revision: 49
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 614a57100ffa8e66b1f03757355605409ac5848f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdatabasemirroringendpoints-transact-sql"></a>sys.database_mirroring_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンスのミラーリング エンドポイントのデータベースに 1 行を含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
> [!NOTE]  
>  データベース ミラーリング エンドポイントは、両方のセッションのミラーリング監視サーバーとデータベース ミラーリング パートナー間および Always On 可用性グループのプライマリ レプリカとセカンダリ レプリカ間のセッションをサポートします。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<継承された列 >**|—|列を継承**sys.endpoints** (詳細については、次を参照してください。 [sys.endpoints &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md))。|  
|**role**|**tinyint**|ミラーリング ロール。次のいずれかになります。<br /><br /> **0** = なし<br /><br /> **1**パートナーを =<br /><br /> **2** = ミラーリング監視サーバー<br /><br /> **3** = all<br /><br /> 注: この値はデータベース ミラーリングのみ関連します。|  
|**role_desc**|**nvarchar(60)**|ミラーリング ロールの説明。次のいずれかになります。<br /><br /> **NONE**<br /><br /> **パートナー**<br /><br /> **ミラーリング監視サーバー**<br /><br /> **ALL**<br /><br /> 注: この値はデータベース ミラーリングのみ関連します。|  
|**is_encryption_enabled**|**bit**|**1**その暗号化が有効になっていることを意味します。<br /><br /> **0**その暗号化が無効になっていることを意味します。|  
|**connection_auth**|**tinyint**|エンドポイントへの接続に必要な接続認証の種類。次のいずれかになります。<br /><br /> **1** - NTLM<br /><br /> **2** -KERBEROS<br /><br /> **3** -NEGOTIATE<br /><br /> **4** -証明書<br /><br /> **5** -NTLM、CERTIFICATE<br /><br /> **6** -KERBEROS、CERTIFICATE<br /><br /> **7** -NEGOTIATE、CERTIFICATE<br /><br /> **8** -CERTIFICATE、NTLM<br /><br /> **9** -証明書、KERBEROS<br /><br /> **10** -CERTIFICATE、NEGOTIATE|  
|**connection_auth_desc**|**nvarchar (60)**|エンドポイントへの接続に必要な認証の種類の説明。次のいずれかになります。<br /><br /> NTLM<br /><br /> KERBEROS<br /><br /> NEGOTIATE<br /><br /> CERTIFICATE<br /><br /> NTLM、CERTIFICATE<br /><br /> KERBEROS、CERTIFICATE<br /><br /> NEGOTIATE、CERTIFICATE<br /><br /> CERTIFICATE、NTLM<br /><br /> CERTIFICATE、KERBEROS<br /><br /> CERTIFICATE、NEGOTIATE|  
|**certificate_id**|**int**|認証で使用される証明書の ID (存在する場合)。<br /><br /> 0 = Windows 認証が使用されます。|  
|**encryption_algorithm**|**tinyint**|暗号化アルゴリズム。次のいずれかになります。<br /><br /> **0** : NONE<br /><br /> **1** – RC4<br /><br /> **2** – AES<br /><br /> **3** – NONE、RC4<br /><br /> **4** – NONE、AES<br /><br /> **5** – RC4、AES<br /><br /> **6** – AES、RC4<br /><br /> **7** – NONE、RC4、AES<br /><br /> **8** – NONE、AES、RC4|  
|**encryption_algorithm_desc**|**nvarchar(60)**|暗号化アルゴリズムの説明。次のいずれかになります。<br /><br /> なし<br /><br /> RC4<br /><br /> AES<br /><br /> NONE、RC4<br /><br /> NONE、AES<br /><br /> RC4、AES<br /><br /> AES、RC4<br /><br /> NONE、RC4、AES<br /><br /> NONE、AES、RC4|  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]  
>  RC4 アルゴリズムは、旧バージョンとの互換性のためにのみサポートされています。 データベース互換性レベルが 90 または 100 の場合、新しい素材は RC4 または RC4_128 を使用してのみ暗号化できます  (非推奨)。AES アルゴリズムのいずれかなど、新しいアルゴリズムを使用してください。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]どの互換性レベル以降では、RC4 または RC4_128 を使用して暗号化された素材を解除できます。  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [追加または可用性レプリカを変更する場合のエンドポイント URL を指定&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)   
 [sys.availability_replicas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [sys.database_mirroring &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md)   
 [sys.database_mirroring_witnesses &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [データベース ミラーリング エンドポイント & #40 です。SQL Server & #41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
