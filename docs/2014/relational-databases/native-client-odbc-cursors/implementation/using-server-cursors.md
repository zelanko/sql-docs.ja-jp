---
title: サーバー カーソルの使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC applications, cursors
- cursors [ODBC], server cursors
- ODBC cursors, server cursors
- server cursors [SQL Server]
ms.assetid: 8a6d99b7-10b8-4474-8639-4914b25ba170
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14e3a92f31f4e494fc722eb3d12feb8e70252728
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427871"
---
# <a name="using-server-cursors"></a>サーバー カーソルの使用
  ODBC アプリケーションの既定値以外に、ODBC カーソル属性のいずれかが設定されている場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、同じ種類の API サーバー カーソルを実装するためにサーバーを要求します。 API サーバー カーソルを使用すると、クライアント側のメモリを解放でき、クライアントとサーバー間のネットワーク トラフィックを大幅に削減できます。  
  
 API サーバー カーソルの潜在的な欠点は、現時点では、すべての SQL ステートメントをサポートしているわけではないことです。 次の機能は、API サーバー カーソルでは実行できません。  
  
-   複数の結果セットを返すバッチまたはストアド プロシージャ  
  
-   COMPUTE 句、COMPUTE BY 句、FOR BROWSE 句、または INTO 句を伴う SELECT ステートメント  
  
-   リモート ストアド プロシージャを参照する EXECUTE ステートメント  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続している場合、サーバー カーソルを使用してこのような特性のステートメントを実行すると、カーソルは既定の結果セットに変換されます。 以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に接続している場合は、エラーになります。  
  
## <a name="see-also"></a>参照  
 [カーソルの実装方法](how-cursors-are-implemented.md)  
  
  
