---
title: SQL 特殊カラム |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7c683e92665257aea7b87bb5107ffe71331ee1b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292252"
---
# <a name="sqlspecialcolumns"></a>SQLSpecialColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  行識別子 (*識別子タイプ*SQL_BEST_ROWID) を要求すると **、要求**されたスコープ以外の空の結果セット (データ行なし) が返SQL_SCOPE_CURROW。 生成される結果セットは、列がこのスコープ内でのみ有効であることを示します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、識別子の擬似列がサポートされません。 **SQLSpecialColumns 結果**セットは、すべての列をSQL_PC_NOT_PSEUDOとして識別します。  
  
 **SQL 特殊列は**、静的カーソルで実行できます。 更新可能な (キーセットドリブンまたは動的) に対して**SQLSpecialColumns**を実行しようとすると、カーソルの種類が変更されたことを示すSQL_SUCCESS_WITH_INFOが返されます。  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>SQLSpecialColumns による機能強化された日付と時刻のサポート  
 日付/時刻型の列DATA_TYPE、TYPE_NAME、COLUMN_SIZE、BUFFER_LENGTH、およびDECIMAL_DIGTSに対して返される値については、「カタログ[メタデータ](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md)」を参照してください。  
  
 詳細については、「 ODBC [&#41;&#40;日付と時刻の向上](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>SQLSpecialColumns による大きな CLR UDT のサポート  
 **SQLSpecialColumns は、** 大規模な CLR ユーザー定義型 (UDT) をサポートします。 詳細については、「 [ODBC&#41;&#40;大規模な CLR ユーザー定義型](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [特別な列関数](https://go.microsoft.com/fwlink/?LinkId=59371)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
