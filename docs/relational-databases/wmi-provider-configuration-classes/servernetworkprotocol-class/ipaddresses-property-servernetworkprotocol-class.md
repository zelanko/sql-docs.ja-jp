---
title: IpAddresses プロパティ (ServerNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- IpAddresses Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- IpAddresses property
ms.assetid: e5d66f7e-9719-436e-b723-12d56f914a05
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5e4f3b59530d7c0a9674a8070387c846d3d1fdd9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750067"
---
# <a name="ipaddresses-property-servernetworkprotocol-class"></a>IpAddresses プロパティ (ServerNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  サーバー ネットワーク プロトコルに関連付けられた IP アドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.IpAddresses [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 のインスタンスによって使用されるネットワークプロトコルを表す**Servernetworkprotocol**オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サーバーネットワークプロトコルによってサポートされる IP アドレスを表す[ServerNetworkProtocolIPAdress クラス](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md)オブジェクトの配列。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
