---
title: MultiIpConfigurationSupport プロパティ (ServerNetworkProtocol クラス) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- MultiIpConfigurationSupport property
ms.assetid: 442c6133-4038-42db-a67d-2631285ac76b
caps.latest.revision: 31
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 876a5988a557a54133c6485f027b58ab13c74a11
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="multiipconfigurationsupport-property-servernetworkprotocol-class"></a>MultiIpConfigurationSupport プロパティ (ServerNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  複数の IP アドレスがサーバー ネットワーク プロトコルによってサポートされるかどうかを指定するブール型のプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.MultiIpConfigurationSupport [= value]  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 A [ProtocolName プロパティ (ServerNetworkProtocol クラス)](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/protocolname-property-servernetworkprotocol-class.md)のインスタンスによって使用されるネットワーク プロトコルを表すオブジェクト[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 複数の IP アドレスがサーバー ネットワーク プロトコルによってサポートされているかどうかを指定するブール値: **true**複数の IP アドレスがサーバー ネットワーク プロトコルによってサポートされている場合または**false**場合複数の IP アドレスは、サーバー ネットワーク プロトコルによってサポートされていません。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
