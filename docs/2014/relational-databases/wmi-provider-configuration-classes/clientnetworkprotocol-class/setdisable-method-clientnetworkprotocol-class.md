---
title: SetDisable メソッド (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDisable Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: bce69ab9-ea5b-43fd-8114-08b1b5890755
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 7b37e2cd0b3342d6ecb520add0bbe4fd533e786a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63192862"
---
# <a name="setdisable-method-clientnetworkprotocol-class"></a>SetDisable メソッド (ClientNetworkProtocol クラス)
  [クライアントプロトコルの構成](https://technet.microsoft.com/library/ms181035.aspx)によって指定されたクライアントネットワークプロトコルを無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a>要素  
 *素材*  
 クライアントによって[!INCLUDE[msCoName](../../../includes/msconame-md.md)]使用されるネットワークプロトコルを表す[clientnetworkprotocol クラス](clientnetworkprotocol-class.md)オブジェクト。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 
  `uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [クライアントのネットワーク プロトコルと Net-Library の構成](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
