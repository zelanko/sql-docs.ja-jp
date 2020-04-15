---
title: データ型の使用 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data types
- ODBC data types, about ODBC data types
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC]
- SQL Server Native Client ODBC driver, data types
- data types [ODBC], about data types
ms.assetid: 4f19b0d6-94ac-4a98-a121-57d38787864c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0384857c53e898af9fca89bb2ee2351f0b65f986
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297859"
---
# <a name="data-type-usage"></a>データ型の使用方法
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ドライバーとデータ型の次の使用を課します。  
  
|データ型|制限事項|  
|---------------|----------------|  
|日付リテラル|日付リテラルは、SQL_TYPE_TIMESTAMP列[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**(datetime**または**smalldatetime**のデータ型) に格納されている場合、時刻値は午前 12:00:00.000 です。|  
|**お金**と**小さなお金**|**お金**と**小金**のデータ型の整数部分だけが重要です。 データ型変換中に SQL **Money**データの小数点部分が切り[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]捨てられると、ネイティブ クライアント ODBC ドライバはエラーではなく警告を返します。|  
|SQL_BINARY (NULL 値を許容)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 以前のインスタンスに接続していて、SQL_BINARY 型の列で NULL 値が許容される場合、データ ソースに格納されているデータには 0 が埋め込まれません。 このような列のデータが取得されると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは、右側にゼロを埋め込みます。 ただし、連結など、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により実行される操作で作成されるデータには、このような埋め込みは行われません。<br /><br /> また、データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 以前のインスタンスの列に格納するときに、そのデータが長すぎて列に収まりきらない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はデータを右側から切り捨てます。<br /><br /> 注:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]6.5 以前への接続をサポートしています。|  
|SQL_CHAR (切り捨て)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 以前のインスタンスに接続し、データを SQL_CHAR 型の列に格納するときに、そのデータが長すぎて列に収まりきらない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では警告を通知せずにデータを右側から切り捨てます。<br /><br /> 注:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]6.5 以前への接続をサポートしています。|  
|SQL_CHAR (NULL 値を許容)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 以前のインスタンスに接続していて、SQL_CHAR 型の列で NULL 値が許容される場合、データ ソースに格納されているデータには空白が埋め込まれません。 このような列のデータが取得されると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは右側に空白を埋め込みます。 ただし、連結など、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により実行される操作で作成されるデータには、このような埋め込みは行われません。<br /><br /> 注:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]6.5 以前への接続をサポートしています。|  
|SQL_LONGVARBINARY、SQL_LONGVARCHAR、SQL_WLONGVARCHAR|SQL_LONGVARBINARY、SQL_LONGVARCHAR、またはSQL_WLONGVARCHARデータ型 (WHERE 句を使用) を使用して、複数の行に影響を与える列の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]更新は、6 のインスタンスに接続すると完全にサポートされます。*x*以降。 4.2 x[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに*x*接続すると、S1000 エラーが発生しました。 text または image 列の挿入または更新に失敗しました。" が返されます。<br /><br /> 注:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]6.5 以前への接続をサポートしています。|  
|文字列関数パラメーター|文字列関数の*string_exp*パラメータは、データ型SQL_CHARまたはSQL_VARCHARである必要があります。 SQL_LONG_VARCHAR データ型はサポートされません。 SQL_CHARおよびSQL_VARCHARデータ・タイプは最大 8,000 文字に制限されているため *、count*パラメーターは 8,000 以下でなければなりません。|  
|時刻リテラル|時刻リテラルは、SQL_TIMESTAMP列[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**(datetime**または**smalldatetime**のデータ型) に格納されている場合、日付値は 1900 年 1 月 1 日になります。|  
|**タイムスタンプ**|**手動でタイムスタンプ**列に挿入できるのは、NULL 値だけです。 ただし、**タイムスタンプ**列は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって自動的に更新されるため、NULL 値は上書きされます。|  
|**tinyint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **tinyint**データ型は符号なしです。 **tinyint**列は、既定でデータ型の変数SQL_C_UTINYINTバインドされます。|  
|エイリアス データ型|4.2 x[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに*x*接続すると、ODBC ドライバーは、列の NULL 値を明示的に宣言しない列定義に NULL を追加します。 したがって、別名データ型の定義に格納されている NULL 値の許容属性は無視されます。<br /><br /> 4.2 x[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに*x*接続すると、基本データ型**が char**または**binary**の別名データ型を持ち、null 許容が宣言されていない別名データ型の列は、データ型**varchar**または**varbinary**として作成されます。 [SQLCol 属性](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) [、SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md)、および[SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md)は、これらの列のデータ型としてSQL_VARCHARまたはSQL_VARBINARYを返します。 これらの列から取得するデータには、埋め込みは行われません。<br /><br /> 注:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]6.5 以前への接続をサポートしています。|  
|LONG データ型|*実行時のデータ*パラメーターは、SQL_LONGVARBINARYとSQL_LONGVARCHARの両方のデータ型に制限されます。|  
|大きな値型|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは、ODBC SQL データ型を受け入れるか返す API で **、varchar(max)** 型 **、varbinary(max)** 型 、**および nvarchar(max)** 型を SQL_VARCHAR 型、SQL_VARBINARY型型、および SQL_WVARCHAR型として公開します。|  
|ユーザー定義型 (UDT)|UDT 列は SQL_SS_UDT としてマップされます。 SQL ステートメントで、UDT の ToString() メソッドまたは ToXMLString() メソッドを使用するか、CAST/CONVERT 関数を使用して UDT 列を明示的に別の型にマップする場合、結果セット内の列の型には変換された列の実際の型が反映されます。<br /><br /> ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC ドライバーは、バイナリとして UDT 列にのみバインドできます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされるのは、SQL_SS_UDT データ型と SQL_C_BINARY データ型の間の変換のみです。|  
|XML|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、XML を Unicode テキストに自動的に変換します。 XML 型は SQL_SS_XML としてマップされます。|  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;結果の処理](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
