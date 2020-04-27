---
title: SetNumValue メソッド (ClientNetworkProtocolProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetNumValue Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetNumValue method
ms.assetid: c292e2ae-6d0a-44ad-ba54-5b0bd705ef37
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: faf680e657cc533f9874b0d041aac0d3fe29f34b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63245003"
---
# <a name="setnumvalue-method-clientnetworkprotocolproperty-class"></a>SetNumValue メソッド (ClientNetworkProtocolProperty クラス)
  [Propertyidx プロパティ (ClientNetworkProtocolProperty クラス)](clientnetworkprotocolproperty-class.md)の値によって参照される、現在のプロパティの数値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.SetNumValue [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 クライアントによって[!INCLUDE[msCoName](../../../includes/msconame-md.md)]使用されるネットワークプロトコルの属性を表す[clientnetworkprotocolproperty クラス](clientnetworkprotocolproperty-class.md)オブジェクト。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*value*|参照されたプロパティの数値を指定する `uint32` 値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 `uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルの構成](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
