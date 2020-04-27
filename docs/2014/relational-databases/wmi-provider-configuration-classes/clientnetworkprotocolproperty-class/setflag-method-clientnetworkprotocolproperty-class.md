---
title: SetFlag メソッド (ClientNetworkProtocolProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetFlag Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetFlag method
ms.assetid: 0407520f-2f84-4f68-b2b7-429697286c1b
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6c33eca0bf3281243aeee42ed89001cf9108d5d4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63245088"
---
# <a name="setflag-method-clientnetworkprotocolproperty-class"></a>SetFlag メソッド (ClientNetworkProtocolProperty クラス)
  [Propertyidx プロパティ (ClientNetworkProtocolProperty クラス)](clientnetworkprotocolproperty-class.md)の値によって参照される現在のプロパティのフラグを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.SetFlag(  
BoolValue  
) [=]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 クライアントによって[!INCLUDE[msCoName](../../../includes/msconame-md.md)]使用されるネットワークプロトコルの属性を表す[clientnetworkprotocolproperty クラス](clientnetworkprotocolproperty-class.md)オブジェクト。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*ブール値*|フラグの新しい値を指定するブール値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 `uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルの構成](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
