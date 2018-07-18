---
title: 結果セット (ODBC) の情報の取得 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a814a65419026dfb6e7901f2b49db2096c5da423
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409642"
---
# <a name="retrieve-result-set-information-odbc"></a>結果セットの情報の取得 (ODBC)
    
### <a name="to-get-information-about-a-result-set"></a>結果セットに関する情報を取得するには  
  
1.  呼び出す[SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md)を結果セットの列の数を取得します。  
  
2.  結果セット内の各列に対して次の操作を行います。  
  
    -   呼び出す[SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md)結果列に関する情報を取得します。  
  
     スイッチまたは  
  
    -   呼び出す[SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md)結果列に関する具体的な記述子情報を取得します。  
  
## <a name="see-also"></a>参照  
 [結果の操作方法に関するトピックを処理&#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)   
 [結果セットの特性の決定&#40;ODBC&#41;](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
