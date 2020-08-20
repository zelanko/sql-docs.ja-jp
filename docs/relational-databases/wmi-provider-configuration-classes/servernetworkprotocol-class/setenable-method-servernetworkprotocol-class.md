---
description: SetEnable メソッド (ServerNetworkProtocol クラス)
title: SetEnable メソッド (ServerNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetEnable Method (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetEnable method
ms.assetid: a287950b-086f-4b6d-a2d8-4d3973bd1b21
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 34ddb0d6220decf65a9a94f8313c3227bca917bc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488426"
---
# <a name="setenable-method-servernetworkprotocol-class"></a>SetEnable メソッド (ServerNetworkProtocol クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  サーバー ネットワーク プロトコルを有効にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetEnable()  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 のインスタンスによって使用されるネットワークプロトコルを表す [Servernetworkprotocol クラス](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/servernetworkprotocol-class.md) オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
