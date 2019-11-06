---
title: カーソル プログラミングの詳細 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- ODBC cursors, programming
- cursors [ODBC], programming
ms.assetid: 6bae29c4-7f49-419c-8712-90db734f992e
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fb462ac3b2b60e405fc8c2753d9fc1395f6d1ecd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68092905"
---
# <a name="cursor-programming-details-odbc"></a>カーソル プログラミングの詳細 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  適切なカーソルの種類を選択することで、アプリケーションのパフォーマンスを向上することができます。 ただし、ある条件下では、要求したカーソルの種類でサポートされていない SQL ステートメントを実行すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によりカーソルの種類が暗黙的に変換されることがあります。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [暗黙のカーソル変換&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/implicit-cursor-conversions-odbc.md)  
  
-   [Autofetch と ODBC カーソルの併用](../../../relational-databases/native-client-odbc-cursors/programming/using-autofetch-with-odbc-cursors.md)  
  
-   [高速順方向専用カーソル&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/fast-forward-only-cursors-odbc.md)  
  
## <a name="see-also"></a>関連項目  
 [カーソルを使用して&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
