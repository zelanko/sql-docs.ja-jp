---
title: PropertyValType プロパティ (ServerNetworkProtocolProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- PropertyValType Property (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyValType property
ms.assetid: fbd42e8e-0642-4a19-b3c8-6ce88345145f
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 4a69cb8f0817c086537381a87b96dfb237b8d59c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62643197"
---
# <a name="propertyvaltype-property-servernetworkprotocolproperty-class"></a>PropertyValType プロパティ (ServerNetworkProtocolProperty クラス)
  参照されたプロパティに格納される値のデータ型を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.PropertyValType [= value]  
```  
  
## <a name="parts"></a>要素  
 *素材*  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)]の[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンス上のネットワークプロトコルの属性を表す[servernetworkprotocolproperty クラス](servernetworkprotocolproperty-class.md)オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 プロパティ値のデータ型を指定する `uint32` 値。 文字列型の値の場合は 0、数値型の値の場合は 1 を返します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
