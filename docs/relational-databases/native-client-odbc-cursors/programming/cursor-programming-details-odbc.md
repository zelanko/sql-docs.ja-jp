---
title: カーソル プログラミングの詳細 (ODBC) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-cursors
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- ODBC cursors, programming
- cursors [ODBC], programming
ms.assetid: 6bae29c4-7f49-419c-8712-90db734f992e
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a1314d2693be5e78bdf00a830bfddf3faabcacea
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707190"
---
# <a name="cursor-programming-details-odbc"></a>カーソル プログラミングの詳細 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  適切なカーソルの種類を選択することで、アプリケーションのパフォーマンスを向上することができます。 ただし、ある条件下では、要求したカーソルの種類でサポートされていない SQL ステートメントを実行すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によりカーソルの種類が暗黙的に変換されることがあります。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [暗黙のカーソル変換&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/implicit-cursor-conversions-odbc.md)  
  
-   [Autofetch と ODBC カーソルの併用](../../../relational-databases/native-client-odbc-cursors/programming/using-autofetch-with-odbc-cursors.md)  
  
-   [高速順方向専用カーソル&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/fast-forward-only-cursors-odbc.md)  
  
## <a name="see-also"></a>参照  
 [カーソルを使用して&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
