---
title: NumberOfFlags プロパティ (ClientNetworkProtocol クラス) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- NumberOfFlags Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- NumberOfFlags property
ms.assetid: 7a656644-2154-419f-9787-99877f597770
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e2d483fc4916be6175093cd68470a57819544ae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177687"
---
# <a name="numberofflags-property-clientnetworkprotocol-class"></a>NumberOfFlags プロパティ (ClientNetworkProtocol クラス)
  によって指定されたクライアント ネットワーク プロトコルに必要なフラグ オプションの数を取得、 [SetOrderValue メソッド (ClientNetworkProtocol クラス)](clientnetworkprotocol-class.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.NumberofFlags [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 [クライアントによって使用されるネットワーク プロトコルを表す](clientnetworkprotocol-class.md) ClientNetworkProtocol クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 `Uint32` プロパティによって参照されるクライアント ネットワーク プロトコルに必要なフラグ オプションの数を指定する `OrderValue` 値。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルの構成](http://technet.microsoft.com/library/ms181035.aspx)  
  
  