---
title: MultiIpConfigurationSupport プロパティ (ServerNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- MultiIpConfigurationSupport property
ms.assetid: 442c6133-4038-42db-a67d-2631285ac76b
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 49b98a6680ba05e13b9fe0ea76a1d445f0d57200
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2018
ms.locfileid: "51217710"
---
# <a name="multiipconfigurationsupport-property-servernetworkprotocol-class"></a>MultiIpConfigurationSupport プロパティ (ServerNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  複数の IP アドレスがサーバー ネットワーク プロトコルによってサポートされるかどうかを指定するブール型のプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.MultiIpConfigurationSupport [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 A [ProtocolName プロパティ (ServerNetworkProtocol クラス)](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/protocolname-property-servernetworkprotocol-class.md)のインスタンスによって使用されるネットワーク プロトコルを表すオブジェクトを[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 複数の IP アドレスがサーバー ネットワーク プロトコルによってサポートされるかどうかを指定するブール値: **true**複数の IP アドレスがサーバー ネットワーク プロトコルによってサポートされている場合または**false**場合複数の IP アドレスは、サーバー ネットワーク プロトコルによってサポートされていません。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
