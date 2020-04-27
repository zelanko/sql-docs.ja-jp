---
title: MultiIpConfigurationSupport プロパティ (ServerNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- MultiIpConfigurationSupport property
ms.assetid: 442c6133-4038-42db-a67d-2631285ac76b
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 3a6813371e7641af1369f94f875ca0d9f96ad3a3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62470059"
---
# <a name="multiipconfigurationsupport-property-servernetworkprotocol-class"></a>MultiIpConfigurationSupport プロパティ (ServerNetworkProtocol クラス)
  複数の IP アドレスがサーバー ネットワーク プロトコルによってサポートされるかどうかを指定するブール型のプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.MultiIpConfigurationSupport [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 のインスタンスによって使用されるネットワークプロトコルを表す[Protocolname プロパティ (ServerNetworkProtocol クラス)](servernetworkprotocol-class.md) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 複数の IP アドレスがサーバー ネットワーク プロトコルによってサポートされるかどうかを指定するブール値。複数の IP アドレスがサーバー ネットワーク プロトコルによってサポートされる場合は `true`、複数の IP アドレスがサーバー ネットワーク プロトコルによってサポートされない場合は `false` です。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
