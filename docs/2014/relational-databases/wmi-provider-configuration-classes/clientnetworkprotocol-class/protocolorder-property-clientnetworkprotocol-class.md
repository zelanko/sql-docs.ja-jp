---
title: ProtocolOrder プロパティ (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ProtocolOrder Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProtocolOrder property
ms.assetid: aa09b8ab-37db-4406-8973-acf503855fd2
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 0a0043e5a894e3f3f1b778a6f42fe6e3bacbbc78
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63192884"
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a>ProtocolOrder プロパティ (ClientNetworkProtocol クラス)
  [Setordervalue メソッド (ClientNetworkProtocol クラス)](clientnetworkprotocol-class.md)メソッドによって指定された現在参照されているクライアントネットワークプロトコルの順序番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 クライアントによって[!INCLUDE[msCoName](../../../includes/msconame-md.md)]使用されるネットワークプロトコルを表す[clientnetworkprotocol クラス](clientnetworkprotocol-class.md)オブジェクト。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 現在参照されているクライアント ネットワーク プロトコルに対して、`uint32` メソッドによって設定されている順序番号を指定する `OrderValue` 値。 クライアント ネットワーク プロトコルが無効の場合、この値は 0 になります。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>参照  
 [クライアントプロトコルの構成](https://technet.microsoft.com/library/ms181035.aspx)   
 [クライアントのネットワーク プロトコルと Net-Library の構成](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
