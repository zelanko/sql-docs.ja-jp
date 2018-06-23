---
title: SetDisable メソッド (ServerNetworkProtocol クラス) |Microsoft ドキュメント
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
- SetDisable Method (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: 0ebbe0c5-07ad-4a76-a918-e379930adf71
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 486157219bfea29653ff3ba1af0a8c69287ef27c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085835"
---
# <a name="setdisable-method-servernetworkprotocol-class"></a>SetDisable メソッド (ServerNetworkProtocol クラス)
  サーバー ネットワーク プロトコルを無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a>要素  
 *object*  
 [ServerNetworkProtocol クラス] servernetworkprotocol-class.md) のインスタンスによって使用されるネットワーク プロトコルを表すオブジェクト[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 uint32 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  