---
title: Properties プロパティ (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 1464f236966f830125e62da65b3a645c99374a11
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219948"
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
  
  
