---
title: SQLSpecialColumns |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1bc1cb10816f407bed89e65ccc5e8927c82442b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408031"
---
# <a name="sqlspecialcolumns"></a>SQLSpecialColumns
  行識別子を要求するとき (*IdentifierType* SQL_BEST_ROWID)、 **SQLSpecialColumns** SQL_SCOPE_CURROW 以外のスコープ、要求された空の結果セット (データ行を含まない) を返します。 生成される結果セットは、列がこのスコープ内でのみ有効であることを示します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、識別子の擬似列がサポートされません。 **SQLSpecialColumns**結果セットでは、すべての列は SQL_PC_NOT_PSEUDO として識別します。  
  
 **SQLSpecialColumns**静的カーソルで実行できます。 実行しようとすると、 **SQLSpecialColumns**で更新可能な (キーセット ドリブンまたは動的) 返しますが、カーソルの種類を示す SQL_SUCCESS_WITH_INFO が変更されました。  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>SQLSpecialColumns による機能強化された日付と時刻のサポート  
 値について返される列の DATA_TYPE、TYPE_NAME、COLUMN_SIZE、buffer_length 列、および decimal_digts の各日付/時刻型を参照してください。[カタログ メタデータ](../native-client-odbc-date-time/metadata-catalog.md)します。  
  
 詳細については、次を参照してください。[日付と時刻の強化&#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)します。  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>SQLSpecialColumns による大きな CLR UDT のサポート  
 **SQLSpecialColumns**大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型&#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)します。  
  
## <a name="see-also"></a>参照  
 [SQLSpecialColumns 関数](http://go.microsoft.com/fwlink/?LinkId=59371)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
