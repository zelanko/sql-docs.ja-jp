---
title: カーソルプログラミングの詳細 (ODBC) |Microsoft Docs
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
ms.openlocfilehash: ddeee2e1c979a22f45aea8f4ba7279447c733df3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73784452"
---
# <a name="cursor-programming-details-odbc"></a>カーソル プログラミングの詳細 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  適切なカーソルの種類を選択することで、アプリケーションのパフォーマンスを向上することができます。 ただし、ある条件下では、要求したカーソルの種類でサポートされていない SQL ステートメントを実行すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によりカーソルの種類が暗黙的に変換されることがあります。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [ODBC&#41;&#40;の暗黙的なカーソル変換](../../../relational-databases/native-client-odbc-cursors/programming/implicit-cursor-conversions-odbc.md)  
  
-   [autofetch と ODBC カーソルの併用](../../../relational-databases/native-client-odbc-cursors/programming/using-autofetch-with-odbc-cursors.md)  
  
-   [ODBC&#41;&#40;高速順方向専用カーソル](../../../relational-databases/native-client-odbc-cursors/programming/fast-forward-only-cursors-odbc.md)  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;カーソルの使用](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
