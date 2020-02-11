---
title: availability_group_listeners (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- availability_group_listeners_TSQL
- sys.availability_group_listeners
- sys.availability_group_listeners_TSQL
- availability_group_listeners
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_group_listeners catalog view
- Availability Groups [SQL Server], listeners
ms.assetid: b5e7d1fb-3ffb-4767-8135-604c575016b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b363e410f35eb7880933520dd1dbf47f258b651e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041061"
---
# <a name="sysavailability_group_listeners-transact-sql"></a>availability_group_listeners (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  各 AlwaysOn 可用性グループについて、可用性グループにネットワーク名が関連付けられていないことを示すゼロ行を返すか、Windows Server フェールオーバー クラスタリング (WSFC) クラスター内の可用性グループ リスナーの構成ごとに 1 行のデータを返します。 このビューには、クラスターから収集されたリアルタイム構成が表示されます。  
  
> [!NOTE]  
>  このカタログビューでは、WSFC クラスターで定義された IP 構成の詳細は説明されていません。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**group_id**|**UNIQUEIDENTIFIER**|[Availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)からの可用性グループ ID (**group_id**)。|  
|**listener_id**|**nvarchar (36)**|クラスターリソース ID からの GUID。|  
|**dns_name**|**nvarchar (63)**|可用性グループリスナーの構成されたネットワーク名 (ホスト名)。|  
|**ポート**|**int**|可用性グループ リスナーに対して構成された TCP ポート番号。<br /><br /> NULL = リスナーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の外部で構成され、そのポート番号が可用性グループに追加されていません。 ポートを追加するには、 [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントの MODIFY LISTENER オプションを使用します。|  
|**is_conformant**|**bit**|この IP 構成が準拠しているかどうか。次のいずれかになります。<br /><br /> 1 = リスナーは準拠しています。 インターネットプロトコル (IP) アドレスの間には、"OR" 関係のみが存在します。 *準拠*には、 [CREATE AVAILABILITY GROUP](../../t-sql/statements/create-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントによって作成されたすべての IP 構成が含まれます。 また、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]外部で作成された ip 構成 (WSFC フェールオーバークラスターマネージャーを使用するなど) が ALTER AVAILABILITY GROUP tsql ステートメントで変更できる場合、ip 構成は準拠として修飾されます。<br /><br /> 0 = リスナーは準拠していません。 通常、これはコマンドを使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]して構成できなかった IP アドレスを示します。代わりに、WSFC クラスターで直接定義されています。|  
|**ip_configuration_string_from_cluster**|**nvarchar(max)**|このリスナーのクラスター IP 構成文字列 (存在する場合)。 NULL = リスナーには仮想 IP アドレスがありません。 次に例を示します。<br /><br /> IPv4 アドレス: `65.55.39.10`<br /><br /> IPv6 アドレス: `2001::4898:23:1002:20f:1fff:feff:b3a3`|  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Always On 可用性グループの動的管理ビューおよび関数 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Always On 可用性グループのカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Transact-sql&#41;&#40;可用性グループの監視](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Always On 可用性グループ &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
