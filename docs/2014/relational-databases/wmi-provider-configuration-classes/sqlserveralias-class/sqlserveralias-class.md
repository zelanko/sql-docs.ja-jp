---
title: SqlServerAlias クラス |Microsoft ドキュメント
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 01e66c9362a8e1c91bd43e4d6821e12f93d23152
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076847"
---
# <a name="sqlserveralias-class"></a>SqlServerAlias クラス
  [SqlServerAlias クラス](sqlserveralias-class.md)クラスは、サーバー接続別名を表します。  
  
 サーバー接続別名は、次の両方に該当する場合に必要となります。  
  
-   インスタンスに、クライアントが接続する[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]既定のネットワーク転送ではないネットワーク トランスポートを経由します。  
  
-   クライアントが接続されている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスが代替の名前付きパイプをリッスンする場合。  
  
 **注:** 、 [SqlServerAlias クラス](sqlserveralias-class.md)継承、`Put`プロバイダー クラスのメソッドです。 ただし、`Provider::Put` メソッドで示される結果は返されません。 詳細については、WMI のドキュメントを参照してください。  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルの構成](http://technet.microsoft.com/library/ms181035.aspx)  
  
  