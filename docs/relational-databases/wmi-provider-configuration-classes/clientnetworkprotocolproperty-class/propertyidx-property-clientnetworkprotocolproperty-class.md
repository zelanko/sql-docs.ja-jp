---
title: PropertyIdx プロパティ (ClientNetworkProtocolProperty クラス) |Microsoft ドキュメント
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
- PropertyIdx Property (ClientNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- PropertyIdx property
ms.assetid: d7845962-ac68-4435-9c59-70ec450fec88
caps.latest.revision: 29
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 52e612599395d2c46ef31bb2e2276bd69227ce8c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="propertyidx-property-clientnetworkprotocolproperty-class"></a>PropertyIdx プロパティ (ClientNetworkProtocolProperty クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  によって参照されるプロパティ配列内のプロパティのインデックス値の設定を取得または、 [Properties プロパティ (ClientNetworkProtocol クラス)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/properties-property-clientnetworkprotocol-class.md)の[ClientNetworkProtocol クラス](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.PropertyIdx [= value]  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 A [ClientNetworkProtocolProperty クラス](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md)によって使用されるネットワーク プロトコルの属性を表すオブジェクト、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]クライアント。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 A **uint32**現在のプロパティの配列のインデックス値を指定する値。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルの構成](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
