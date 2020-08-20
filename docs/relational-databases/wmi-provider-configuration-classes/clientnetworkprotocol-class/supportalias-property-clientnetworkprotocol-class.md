---
description: SupportAlias プロパティ (ClientNetworkProtocol クラス)
title: SupportAlias プロパティ (ClientNetworkProtocol)
ms.custom: seo-lt-2019
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
ms.openlocfilehash: 24eb0c2099dc651ada4d796d9ad65cad747bc67a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485230"
---
# <a name="supportalias-property-clientnetworkprotocol-class"></a>SupportAlias プロパティ (ClientNetworkProtocol クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  [Setordervalue メソッド (ClientNetworkProtocol クラス)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/setordervalue-method-clientnetworkprotocol-class.md)によって指定された現在のネットワークプロトコルがエイリアスをサポートするかどうかを指定するブール型プロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SupportAlias [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 [クライアントによって使用されるネットワーク プロトコルを表す](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) ClientNetworkProtocol クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 クライアント ネットワーク プロトコルが別名をサポートするかどうかを指定するブール値。  
  
 True の場合、クライアント ネットワーク プロトコルは別名をサポートします。  
  
 False の場合、クライアント ネットワーク プロトコルは別名をサポートしません。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルの構成](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
