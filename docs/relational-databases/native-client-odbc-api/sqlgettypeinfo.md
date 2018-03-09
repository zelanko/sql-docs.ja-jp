---
title: "SQLGetTypeInfo |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c59bc2a6f4571d7ceff9b0a6b89328e5fe0095f0
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのレポートの結果に追加される列 USERTYPE が設定**SQLGetTypeInfo**です。 USERTYPE には DB-Library データ型の定義が示されるので、既存の DB-Library アプリケーションを ODBC に移植する開発者にとって便利です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では ID が属性として処理されますが、ODBC ではデータ型として処理されます。 この不一致を解決するのには**SQLGetTypeInfo**データ型を返します: **intidentity**、 **smallintidentity**、 **tinyintidentity**、**decimalidentity**、および**numericidentity**です。 **SQLGetTypeInfo**結果セット列 AUTO_UNIQUE_VALUE がこれらのデータ型の値は TRUE を報告します。  
  
 **Varchar**、 **nvarchar**と**varbinary**、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、column_size 8000、4000、および 8000 をそれぞれレポート引き続き場合でも、実際に限定されるわけでは値です。 これにより、旧バージョンとの互換性が確保されます。  
  
 **Xml**データ型、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、column_size がサイズ無制限を示す SQL_SS_LENGTH_UNLIMITED を報告します。  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo とテーブル値パラメーター  
 テーブル値パラメーターのテーブル型は、実質的にはメタ型 (他の型を定義する際に使用される型) です。 したがって、SQLGetTypeInfo を介して公開することはありません。 アプリケーションでは、テーブル値パラメーターで使用されるテーブル型のメタデータを取得するのに SQLGetTypeInfo ではなく SQLTables を使用する必要があります。  
  
 詳細については、テーブル値パラメーターのメタデータの取得についてを参照してください。[ステートメント属性をその Affect Table-Valued パラメーター](../../relational-databases/native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md)です。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>SQLGetTypeInfo による機能強化された日付と時刻のサポート  
 日付/時刻型に対して返される値は、次を参照してください。[カタログ メタデータ](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md)です。  
  
 一般的な情報について、次を参照してください。[日付と時刻の強化 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>SQLGetTypeInfo による大きな CLR UDT のサポート  
 **SQLGetTypeInfo**大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型 &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLGetTypeInfo 関数](http://go.microsoft.com/fwlink/?LinkId=59356)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
