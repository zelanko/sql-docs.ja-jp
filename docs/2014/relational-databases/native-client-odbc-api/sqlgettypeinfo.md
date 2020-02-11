---
title: SQLGetTypeInfo |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60c4c4d364f9c07e9ca241dd357535f7f7acb42d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046696"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
  Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client ODBC ドライバーは、の`SQLGetTypeInfo`結果セットに列 USERTYPE を追加して報告します。 USERTYPE には DB-Library データ型の定義が示されるので、既存の DB-Library アプリケーションを ODBC に移植する開発者にとって便利です。  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では ID が属性として処理されますが、ODBC ではデータ型として処理されます。 この不一致を解決する`SQLGetTypeInfo`ために、はデータ型**intidentity**、 **smallintidentity**、 **tinyintidentity**、 **decimalidentity**、および**numericidentity**を返します。 結果`SQLGetTypeInfo`セット列 AUTO_UNIQUE_VALUE は、これらのデータ型の値 TRUE を報告します。  
  
 **Varchar**、 **nvarchar** 、および**Varbinary**の場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、Native Client ODBC ドライバーは、実際には無制限であるにもかかわらず、COLUMN_SIZE の値に対してそれぞれ8000、4000、および8000を報告し続けます。 これにより、旧バージョンとの互換性が確保されます。  
  
 **Xml**データ型の場合、NATIVE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client ODBC ドライバーは、サイズを無制限に示す COLUMN_SIZE の SQL_SS_LENGTH_UNLIMITED を報告します。  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo とテーブル値パラメーター  
 テーブル値パラメーターのテーブル型は、実質的には、他の型を定義するために使用される型であるメタ型です。 そのため、SQLGetTypeInfo を介して公開する必要はありません。 アプリケーションでは、テーブル値パラメーターで使用されるテーブル型のメタデータを取得するために、SQLGetTypeInfo ではなく SQLTables を使用する必要があります。  
  
 テーブル値パラメーターのメタデータの取得の詳細については、「[テーブル値パラメーターに影響を与えるステートメント属性](../native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md)」を参照してください。  
  
 テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>SQLGetTypeInfo による機能強化された日付と時刻のサポート  
 日付型または時刻型に対して返される値については、「[カタログメタデータ](../native-client-odbc-date-time/metadata-catalog.md)」を参照してください。  
  
 一般的な情報については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>SQLGetTypeInfo による大きな CLR UDT のサポート  
 
  `SQLGetTypeInfo` は、大きな CLR ユーザー定義型 (UDT) をサポートしています。 詳細については、「[大容量の CLR ユーザー定義型 &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLGetTypeInfo 関数](https://go.microsoft.com/fwlink/?LinkId=59356)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
