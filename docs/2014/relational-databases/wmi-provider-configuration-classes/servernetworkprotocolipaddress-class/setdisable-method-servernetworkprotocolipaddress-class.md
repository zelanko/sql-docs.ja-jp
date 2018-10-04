---
title: SetDisable メソッド (ServerNetworkProtocolIPAddress クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- SetDisable Method (ServerNetworkProtocolIPAddress Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: 7a7cc8cc-9fb8-4bf5-b483-2150d633ee10
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f556620bb66c087aefc87980e42e7d4a7e23443d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48138682"
---
# <a name="setdisable-method-servernetworkprotocolipaddress-class"></a>SetDisable メソッド (ServerNetworkProtocolIPAddress クラス)
  IP アドレスを無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a>要素  
 *object*  
 [ServerNetworkProtocolIPAdress クラス] servernetworkprotocolipaddress-class.md) のインスタンス上のネットワーク プロトコルの IP アドレスを表すオブジェクトを[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 uint32 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
