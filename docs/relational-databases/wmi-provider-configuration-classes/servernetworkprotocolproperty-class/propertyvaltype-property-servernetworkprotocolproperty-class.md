---
description: PropertyValType プロパティ (ServerNetworkProtocolProperty クラス)
title: PropertyValType プロパティ (ServerNetworkProtocolProperty)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- PropertyValType Property (ServerNetworkProtocolProperty
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- PropertyValType property
ms.assetid: fbd42e8e-0642-4a19-b3c8-6ce88345145f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4a74b71b3cfef263a706319ff2ac0500180497c8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485166"
---
# <a name="propertyvaltype-property-servernetworkprotocolproperty-class"></a>PropertyValType プロパティ (ServerNetworkProtocolProperty クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  参照されたプロパティに格納される値のデータ型を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.PropertyValType [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 のインスタンス上のネットワークプロトコルの属性を表す [Servernetworkprotocolproperty クラス](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolproperty-class/servernetworkprotocolproperty-class.md) オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 プロパティ値のデータ型を指定する **uint32** 値。 文字列型の値の場合は 0、数値型の値の場合は 1 を返します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
