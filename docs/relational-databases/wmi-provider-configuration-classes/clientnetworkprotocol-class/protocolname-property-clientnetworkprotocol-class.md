---
title: ProtocolName プロパティ (ClientNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProtocolName Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolName property
ms.assetid: f8527121-fbcd-4d30-9b4a-1461149cb5a8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ddc3dc3d718b67af16af0d213923c94d504af391
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768291"
---
# <a name="protocolname-property-clientnetworkprotocol-class"></a>ProtocolName プロパティ (ClientNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  [クライアントプロトコルの構成](https://technet.microsoft.com/library/ms181035.aspx)によって指定された現在のネットワークプロトコルの名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.ProtocolName [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 クライアントによって使用されるネットワークプロトコルを表す[Clientnetworkprotocol クラス](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md)オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 [Setordervalue メソッド (ClientNetworkProtocol クラス)](https://technet.microsoft.com/library/ms179295.aspx)によって参照される現在のクライアントネットワークプロトコルの名前を指定する文字列値。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [クライアントのネットワーク プロトコルと Net-Library の構成](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
