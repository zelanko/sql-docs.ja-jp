---
title: SQLGetTypeInfo |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
caps.latest.revision: 47
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e83a45cad86f882bfcb1c7cbb15f32736d694d55
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174473"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのレポートの結果に追加される列 USERTYPE が設定`SQLGetTypeInfo`です。 USERTYPE には DB-Library データ型の定義が示されるので、既存の DB-Library アプリケーションを ODBC に移植する開発者にとって便利です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では ID が属性として処理されますが、ODBC ではデータ型として処理されます。 この不一致を解決するのには`SQLGetTypeInfo`データ型を返します: **intidentity**、 **smallintidentity**、 **tinyintidentity**、 **decimalidentity**、および**numericidentity**です。 `SQLGetTypeInfo`結果セット列 AUTO_UNIQUE_VALUE がこれらのデータ型の値は TRUE を報告します。  
  
 **Varchar**、 **nvarchar**と**varbinary**、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、column_size 8000、4000、および 8000 をそれぞれレポート引き続き場合でも、実際に限定されるわけでは値です。 これにより、旧バージョンとの互換性が確保されます。  
  
 **Xml**データ型、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、column_size がサイズ無制限を示す SQL_SS_LENGTH_UNLIMITED を報告します。  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo とテーブル値パラメーター  
 テーブル値パラメーターのテーブル型は、実質的にはメタ型 (他の型を定義する際に使用される型) です。 したがって、SQLGetTypeInfo を介して公開することはありません。 アプリケーションでは、テーブル値パラメーターで使用されるテーブル型のメタデータを取得するのに SQLGetTypeInfo ではなく SQLTables を使用する必要があります。  
  
 詳細については、テーブル値パラメーターのメタデータの取得についてを参照してください。[ステートメント属性をその Affect Table-Valued パラメーター](../native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md)です。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>SQLGetTypeInfo による機能強化された日付と時刻のサポート  
 日付/時刻型に対して返される値は、次を参照してください。[カタログ メタデータ](../native-client-odbc-date-time/metadata-catalog.md)です。  
  
 一般的な情報について、次を参照してください。[日付と時刻の強化&#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>SQLGetTypeInfo による大きな CLR UDT のサポート  
 `SQLGetTypeInfo` は、大きな CLR ユーザー定義型 (UDT) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型&#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLGetTypeInfo 関数](http://go.microsoft.com/fwlink/?LinkId=59356)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  