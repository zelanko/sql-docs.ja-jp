---
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
ms.openlocfilehash: 3fa3ef35a4462eb4cf45df1f4f292be12fb18b25
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758539"
---
# <a name="supportalias-property-clientnetworkprotocol-class"></a>SupportAlias プロパティ (ClientNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
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
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [クライアント プロトコルの構成](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
