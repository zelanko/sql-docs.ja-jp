---
title: プロシージャ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 14ff76504c9a36657be60ba4855cf252474071d7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302373"
---
# <a name="sqlprocedures"></a>SQLProcedures
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャは値を返します。 **SQLProcedures は**、結果セット列のPROCEDURE_TYPEに関するSQL_PT_FUNCTIONを報告します。  
  
 **△カタログ***名、スキーマ名、* または*プロシージャ名*のパラメータに値が存在するかどうかSQL_SUCCESSを返します。 **SQLFetch**は、これらのパラメーターで無効な値が使用されている場合にSQL_NO_DATAを返します。  
  
 **SQL プロシージャは**、静的サーバー カーソルで実行できます。 更新可能 (動的またはキーセット) カーソルに対して**SQLProcedures**を実行しようとすると、SQL_SUCCESS_WITH_INFOが戻され、カーソルの種類が変更されたことを示します。  
  
 **プロシージャは**、名前が*ProcName*と一致し、現在のユーザーが実行できるプロシージャ、または現在のユーザーに VIEW DEFINITION 権限が与えられているプロシージャに関する情報を返します。  
  
## <a name="see-also"></a>参照  
 [プロシージャ関数](https://go.microsoft.com/fwlink/?LinkId=59364)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
