---
title: IpAddresses プロパティ (ServerNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- IpAddresses Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- IpAddresses property
ms.assetid: e5d66f7e-9719-436e-b723-12d56f914a05
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: e7b2adf53bc6ebca14e2d3b4dc2cee248a4b6720
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63190301"
---
# <a name="ipaddresses-property-servernetworkprotocol-class"></a>IpAddresses プロパティ (ServerNetworkProtocol クラス)
  サーバー ネットワーク プロトコルに関連付けられた IP アドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.IpAddresses [= value]  
```  
  
## <a name="parts"></a>要素  
 *素材*  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)]の`ServerNetworkProtocol` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスによって使用されるネットワークプロトコルを表すオブジェクトです。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サーバーネットワークプロトコルによってサポートされる IP アドレスを表す[ServerNetworkProtocolIPAdress クラス](../servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md)オブジェクトの配列。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
