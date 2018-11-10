---
title: SupportAlias プロパティ (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SupportAlias Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SupportAlias property
ms.assetid: 1e7a2e87-c356-40a6-a6d9-e492467629f9
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 86bb264dcf9856d53ed655b15bb2953e4f4819af
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2018
ms.locfileid: "51216370"
---
# <a name="supportalias-property-clientnetworkprotocol-class"></a>SupportAlias プロパティ (ClientNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  現在のネットワーク プロトコルがで指定されたかどうかを指定するブール型プロパティを取得、 [SetOrderValue メソッド (ClientNetworkProtocol クラス)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/setordervalue-method-clientnetworkprotocol-class.md)別名をサポートします。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SupportAlias [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 [クライアントによって使用されるネットワーク プロトコルを表す](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) ClientNetworkProtocol クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 クライアント ネットワーク プロトコルが別名をサポートするかどうかを指定するブール値。  
  
 True の場合、クライアント ネットワーク プロトコルは別名をサポートします。  
  
 False の場合、クライアント ネットワーク プロトコルは別名をサポートしません。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルの構成](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
