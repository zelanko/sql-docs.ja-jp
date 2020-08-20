---
description: SetNumValue メソッド (ClientNetworkProtocolProperty クラス)
title: SetNumValue メソッド (ClientNetworkProtocolProperty)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetNumValue Method (ClientNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetNumValue method
ms.assetid: c292e2ae-6d0a-44ad-ba54-5b0bd705ef37
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7a40a838f9df9621314b87048ec4b5e143f692ce
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472892"
---
# <a name="setnumvalue-method-clientnetworkprotocolproperty-class"></a>SetNumValue メソッド (ClientNetworkProtocolProperty クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  [Propertyidx プロパティ (ClientNetworkProtocolProperty クラス)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/propertyidx-property-clientnetworkprotocolproperty-class.md)の値によって参照される、現在のプロパティの数値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetNumValue [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 クライアントによって使用されるネットワークプロトコルの属性を表す [Clientnetworkprotocolproperty クラス](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*value*|参照されるプロパティの数値を指定する **uint32** 値。|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルの構成](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
