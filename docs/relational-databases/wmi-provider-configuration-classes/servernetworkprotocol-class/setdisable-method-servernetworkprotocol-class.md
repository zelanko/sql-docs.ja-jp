---
title: SetDisable メソッド (ServerNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDisable Method (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDisable method
ms.assetid: 0ebbe0c5-07ad-4a76-a918-e379930adf71
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ebc1e21e4da27504de104c542d58973962827f94
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51667698"
---
# <a name="setdisable-method-servernetworkprotocol-class"></a>SetDisable メソッド (ServerNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  サーバー ネットワーク プロトコルを無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetDisable()  
```  
  
## <a name="parts"></a>要素  
 *object*  
 A [ServerNetworkProtocol クラス](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/servernetworkprotocol-class.md)のインスタンスによって使用されるネットワーク プロトコルを表すオブジェクトを[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 uint32 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
