---
title: PropertyValType プロパティ (ServerNetworkProtocolProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- PropertyValType Property (ServerNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- PropertyValType property
ms.assetid: fbd42e8e-0642-4a19-b3c8-6ce88345145f
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 54ecc89bf7c2674c8913627b0292b267fce9d571
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47836412"
---
# <a name="propertyvaltype-property-servernetworkprotocolproperty-class"></a>PropertyValType プロパティ (ServerNetworkProtocolProperty クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  参照されたプロパティに格納される値のデータ型を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.PropertyValType [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 A [ServerNetworkProtocolProperty クラス](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolproperty-class/servernetworkprotocolproperty-class.md)オブジェクトのインスタンス上のネットワーク プロトコルの属性を表す[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 A **uint32**プロパティの値のデータ型を指定する値。 文字列型の値の場合は 0、数値型の値の場合は 1 を返します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
