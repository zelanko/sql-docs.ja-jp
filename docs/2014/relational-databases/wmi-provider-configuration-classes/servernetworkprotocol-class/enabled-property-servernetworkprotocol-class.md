---
title: Enabled プロパティ (ServerNetworkProtocol クラス) |Microsoft ドキュメント
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
- Enabled Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Enabled property
ms.assetid: a514822a-91f1-4aca-9175-2b96cff29700
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 538215095bb15aa34d95ecab70eec6894055ead0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174884"
---
# <a name="enabled-property-servernetworkprotocol-class"></a>Enabled プロパティ (ServerNetworkProtocol クラス)
  サーバー ネットワーク プロトコルが有効かどうかを指定するブール型のプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.Enabled [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 A [ServerNetworkProtocol クラス](servernetworkprotocol-class.md)のインスタンスによって使用されるネットワーク プロトコルを表すオブジェクト[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サーバー ネットワーク プロトコルが有効かどうかを指定するブール値。サーバー ネットワーク プロトコルが有効な場合は `true`、サーバー ネットワーク プロトコルが無効な場合は `false` です。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  