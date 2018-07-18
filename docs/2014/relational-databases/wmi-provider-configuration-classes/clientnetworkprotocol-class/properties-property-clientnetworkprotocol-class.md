---
title: Properties プロパティ (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Properties Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Properties property
ms.assetid: 7e0a4e38-4555-4750-8fd3-4425b29e6aa1
caps.latest.revision: 33
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 569c1b0f8f140bd05c2be03286e6c9fa1d66a200
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202732"
---
# <a name="properties-property-clientnetworkprotocol-class"></a>Properties プロパティ (ClientNetworkProtocol クラス)
  [Configure Client Protocols (クライアント プロトコルの構成)](http://technet.microsoft.com/library/ms181035.aspx)によって指定された現在のクライアント ネットワーク プロトコルに関連付けられたプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.Properties [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 [クライアントによって使用されるネットワーク プロトコルを表す](clientnetworkprotocol-class.md) ClientNetworkProtocol クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 配列の[ClientNetworkProtocolProperty クラス](../clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md)によって参照される現在のクライアント ネットワーク プロトコルによってサポートされるプロパティを表すオブジェクト、`OrderValue`プロパティ。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [クライアント ネットワーク プロトコルとネットワーク ライブラリの構成](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
