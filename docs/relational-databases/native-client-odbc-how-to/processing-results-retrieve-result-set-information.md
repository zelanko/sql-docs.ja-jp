---
title: 結果セット (ODBC) の情報の取得 |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2211e77ed927c9c2bb5fd9cc3e5df89bc20a5245
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430251"
---
# <a name="processing-results---retrieve-result-set-information"></a>結果の処理 - 結果セットの情報の取得
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
### <a name="to-get-information-about-a-result-set"></a>結果セットに関する情報を取得するには  
  
1.  呼び出す[SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md)を結果セットの列の数を取得します。  
  
2.  結果セット内の各列に対して次の操作を行います。  
  
    -   呼び出す[SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md)結果列に関する情報を取得します。  
  
     スイッチまたは  
  
    -   呼び出す[SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)結果列に関する具体的な記述子情報を取得します。  
  
## <a name="see-also"></a>参照  
[結果を処理&#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/processing-results-process-results.md)

[結果セットの特性の決定&#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
