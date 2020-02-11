---
title: SetStringValue メソッド (ClientNetworkProtocolProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStringValue Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStringValue method
ms.assetid: 88d67b22-0eea-48c9-ab73-e0b4907953df
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 82b89246d6289d0b19ee97e68e94f77d7cb30a77
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63244991"
---
# <a name="setstringvalue-method-clientnetworkprotocolproperty-class"></a>SetStringValue メソッド (ClientNetworkProtocolProperty クラス)
  
  [PropertyIdx プロパティ (ClientNetworkProtocolProperty クラス)](clientnetworkprotocolproperty-class.md) の値によって参照される現在のプロパティの文字列値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.SetStringValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a>要素  
 *素材*  
 クライアントによって[!INCLUDE[msCoName](../../../includes/msconame-md.md)]使用されるネットワークプロトコルの属性を表す[clientnetworkprotocolproperty クラス](clientnetworkprotocolproperty-class.md)オブジェクト。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|[説明]|  
|---------------|-----------------|  
|*StrValue*|現在のプロパティの新しい値を指定する文字列値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 
  `uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルの構成](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
