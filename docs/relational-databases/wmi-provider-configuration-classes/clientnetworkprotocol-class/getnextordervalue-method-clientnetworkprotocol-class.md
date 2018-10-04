---
title: GetNextOrderValue メソッド (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- GetNextOrderValue Method (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- GetNextOrderValue method
ms.assetid: d741dc5c-c225-43d9-a730-7ad664ac525f
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: e43e75b932b719a27eeb164c4555cb1773985cbe
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47824141"
---
# <a name="getnextordervalue-method-clientnetworkprotocol-class"></a>GetNextOrderValue メソッド (ClientNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  プロトコル リスト内で次の位置にあるプロトコルを選択します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.GetNextOrderValue()  
```  
  
## <a name="parts"></a>要素  
 *object*  
 A [ClientNetworkProtocol クラス](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md)によって使用されるネットワーク プロトコルを表すオブジェクトを[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]クライアント。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルを構成します。](http://technet.microsoft.com/library/ms181035.aspx)   
 [クライアント ネットワーク プロトコルとネットワーク ライブラリの構成](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
