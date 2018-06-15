---
title: sys.availability_group_listener_ip_addresses (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- availability_group_listener_ip_addresses
- sys.availability_group_listener_ip_addresses
- availability_group_listener_ip_addresses_TSQL
- sys.availability_group_listener_ip_addresses_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], listeners
- sys.availability_group_listener_ip_addresses catalog view
ms.assetid: e515fa6b-1354-4110-9b70-ab2e6164c992
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4040838a66333fb72ec4f1beb4b55fba7dfe6195
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33180338"
---
# <a name="sysavailabilitygrouplisteneripaddresses-transact-sql"></a>sys.availability_group_listener_ip_addresses (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Always On 可用性グループ リスナーもすべて、Windows Server フェールオーバー クラスタ リング (WSFC) クラスター内に関連付けられている IP アドレスごとに行を返します。  
  
 主キー: **listener_id** + **ip_address** + **ip_sub_mask**  
  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**listener_id**|**nvarchar(36)**|Windows Server フェールオーバー クラスタリング (WSFC) クラスターからのリソース GUID。|  
|**ip_address**|**nvarchar(48)**|可用性グループ リスナーの構成された仮想 IP アドレス。 1 つの IPv4 アドレスまたは IPv6 アドレスを返します。|  
|**ip_subnet_mask**|**nvarchar(15)**|可用性グループ リスナーに対して構成されている IPv4 アドレスの構成された IP サブネット マスク (存在する場合)。<br /><br /> NULL = IPv6 サブネット|  
|**is_dhcp**|**bit**|IP アドレスが DHCP によって構成されているかどうか。次のいずれかになります。<br /><br /> 0 = IP アドレスは DHCP によって構成されていません。<br /><br /> 1 = IP アドレスは DHCP によって構成されています。|  
|**network_subnet_ip**|**nvarchar(48)**|IP アドレスが属するサブネットを指定するネットワーク サブネット IP アドレス。|  
|**network_subnet_prefix_length**|**int**|IP アドレスが属するサブネットのネットワーク サブネット プレフィックス長。|  
|**network_subnet_ipv4_mask**|**nvarchar(45)**|IP アドレスが属するサブネットのネットワーク サブネット マスク。 **network_subnet_ipv4_mask**の WITH DHCP 句で DHCP < network_subnet_option > オプションを指定する、 [CREATE AVAILABILITY GROUP](../../t-sql/statements/create-availability-group-transact-sql.md)または[ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。<br /><br /> NULL = IPv6 サブネット|  
|**状態**|**tinyint**|WSFC のクラスターからの IP リソースのオンラインまたはオフライン状態。次のいずれかになります。<br /><br /> 1 = オンライン。 IP リソースはオンラインです。<br /><br /> 0 = オフライン。 IP リソースはオフラインです。<br /><br /> 2 = オンライン待ち。 IP リソースはオフラインですが、オンラインに移行します。<br /><br /> 3 = 失敗。 IP リソースをオンラインに移行しようとしましたが、失敗しました。|  
|**state_desc**|**nvarchar(60)**|説明**状態**,、1 つの。<br /><br /> ONLINE<br /><br /> OFFLINE<br /><br /> ONLINE_PENDING<br /><br /> FAILED|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
