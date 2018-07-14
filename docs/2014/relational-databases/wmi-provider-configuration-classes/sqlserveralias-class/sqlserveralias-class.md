---
title: SqlServerAlias クラス |Microsoft Docs
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
- SqlServerAlias Class
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServerAlias class
ms.assetid: 475662b9-6985-45bf-b1e9-b0f26ef50443
caps.latest.revision: 33
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 68976bc9c8683554ac58a0744196ecfa5bc7e689
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37274278"
---
# <a name="sqlserveralias-class"></a>SqlServerAlias クラス
  [SqlServerAlias クラス](sqlserveralias-class.md)クラスは、サーバー接続別名を表します。  
  
 サーバー接続別名は、次の両方に該当する場合に必要となります。  
  
-   インスタンスに、クライアントが接続して[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]既定のネットワーク トランスポートではないネットワーク トランスポートを経由します。  
  
-   クライアントが接続されている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスが代替の名前付きパイプをリッスンする場合。  
  
 **注:** 、 [SqlServerAlias クラス](sqlserveralias-class.md)継承、`Put`プロバイダー クラスのメソッド。 ただし、`Provider::Put` メソッドで示される結果は返されません。 詳細については、WMI のドキュメントを参照してください。  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルの構成](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
