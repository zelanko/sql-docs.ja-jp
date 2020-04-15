---
title: をクリックしてください。マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 81ba57c6e66f156f13055ff5ec941fa8f0c86381
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298448"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC ドライバーは **、SQLGetTypeInfo**の結果セットに追加の列 USERTYPE を報告します。 USERTYPE には DB-Library データ型の定義が示されるので、既存の DB-Library アプリケーションを ODBC に移植する開発者にとって便利です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では ID が属性として処理されますが、ODBC ではデータ型として処理されます。 この不一致を解決するために、 **SQLGetTypeInfo**は、データ型を返します: **intid**、**小さな識別**、**タイニント ID、10**進**ID**、および**数値 ID。** **SQLGetTypeInfo**結果セット列AUTO_UNIQUE_VALUE、これらのデータ型の値 TRUE を報告します。  
  
 **varchar** **、nvarchar**および**varbinary**の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは、実際には無制限であっても、COLUMN_SIZE値についてそれぞれ 8000、4000、8000 を報告し続けます。 これにより、旧バージョンとの互換性が確保されます。  
  
 **xml**データ型の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは、COLUMN_SIZEが無制限のサイズを示すSQL_SS_LENGTH_UNLIMITEDを報告します。  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo とテーブル値パラメーター  
 テーブル値パラメーターのテーブル型は、実質的にはメタ型であり、他の型を定義するために使用される型です。 したがって、SQLGetTypeInfo を使用して公開する必要はありません。 アプリケーションは、テーブル値パラメーターで使用されるテーブル型のメタデータを取得するために、SQLGetTypeInfo ではなく SQLTables を使用する必要があります。  
  
 テーブル値パラメーターの metdata の取得については、「テーブル値パラメーターに[影響を与えるステートメント属性](../../relational-databases/native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md)」を参照してください。  
  
 テーブル値パラメーターの詳細については、「 [ODBC&#41;&#40;テーブル値パラメーター ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>SQLGetTypeInfo による機能強化された日付と時刻のサポート  
 日付/時刻型の値が返される場合は、[カタログ メタデータ](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md)を参照してください。  
  
 詳細については、「 ODBC [&#41;&#40;日付と時刻の向上](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>SQLGetTypeInfo による大きな CLR UDT のサポート  
 **大規模**な CLR ユーザー定義型 (UDT) をサポートしています。 詳細については、「 [ODBC&#41;&#40;大規模な CLR ユーザー定義型](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [関数](https://go.microsoft.com/fwlink/?LinkId=59356)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
