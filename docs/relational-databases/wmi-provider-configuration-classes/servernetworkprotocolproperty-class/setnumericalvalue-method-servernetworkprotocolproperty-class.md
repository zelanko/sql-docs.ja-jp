---
description: SetNumericalValue メソッド (ServerNetworkProtocolProperty クラス)
title: SetNumericalValue メソッド (ServerNetworkProtocolProperty)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetNumericalValue Method (ServerNetworkProtocolProperty
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetNumericalValue method
ms.assetid: b3b4bce8-9d9e-4ccb-a223-0454281353b0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7bf6796c663ef0150702077b8c2a48300f0efc9a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488389"
---
# <a name="setnumericalvalue-method-servernetworkprotocolproperty-class"></a>SetNumericalValue メソッド (ServerNetworkProtocolProperty クラス)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  参照されたプロパティの数値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetNumericalValue(NumValue)  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 のインスタンス上のネットワークプロトコルの属性を表す [Servernetworkprotocolproperty クラス](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolproperty-class/servernetworkprotocolproperty-class.md) オブジェクト [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*NumValue*|現在のプロパティの新しい値を指定する **uint32** 値。|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>関連項目  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
