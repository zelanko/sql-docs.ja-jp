---
title: SetEnable メソッド (ServerNetworkProtocolIPAddress クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetEnable Method (ServerNetworkProtocolIPAddress Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEnable method
ms.assetid: baa86deb-95dd-416f-b2c7-cec1dfb91ab4
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d4c542aa1491710d49ec4c24c027e69f2eef24a9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62643124"
---
# <a name="setenable-method-servernetworkprotocolipaddress-class"></a>SetEnable メソッド (ServerNetworkProtocolIPAddress クラス)
  IP アドレスを有効にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.SetEnable()  
  
```  
  
## <a name="parts"></a>要素  
 *素材*  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)]の[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンス上のネットワークプロトコルの IP アドレスを表す[ServerNetworkProtocolIPAdress クラス](servernetworkprotocolipaddress-class.md)オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 
  `uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
