---
description: SetDisable メソッド (ServerNetworkProtocolIPAddress クラス)
title: SetDisable メソッド (ServerNetworkProtocolIPAddress)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDisable Method (ServerNetworkProtocolIPAddress Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDisable method
ms.assetid: 7a7cc8cc-9fb8-4bf5-b483-2150d633ee10
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cd7f7fbc3fb0480183789ec19557b923037d8341
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463573"
---
# <a name="setdisable-method-servernetworkprotocolipaddress-class"></a>SetDisable メソッド (ServerNetworkProtocolIPAddress クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  IP アドレスを無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetDisable()  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 のインスタンス上のネットワークプロトコルの IP アドレスを表す [ServerNetworkProtocolIPAdress クラス](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md) オブジェクト [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 uint32 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
