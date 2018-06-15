---
title: データ型の使用状況 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-results
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e8a08f91688a4a6c26fd138de51ee50b7b2a3974
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32947057"
---
# <a name="data-type-usage"></a>データ型の使用方法
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型の次の使用を強制します。  
  
|データ型|制限事項|  
|---------------|----------------|  
|日付リテラル|Sql_type_timestamp 型の列に格納されているときの日付リテラル ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータ型**datetime**または**smalldatetime**)、12:00:00.000 a.m ですの時刻の値がある。|  
|**money**と**smallmoney**|整数部分だけ、 **money**と**smallmoney**データ型が重要です。 場合は SQL の小数部**money**データ型の変換中にデータが切り捨てられます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、警告、エラーではなくを返します。|  
|SQL_BINARY (NULL 値を許容)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 以前のインスタンスに接続していて、SQL_BINARY 型の列で NULL 値が許容される場合、データ ソースに格納されているデータには 0 が埋め込まれません。 このような列からデータを取得するとき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーが右側のゼロを埋め込みます。 ただし、連結など、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により実行される操作で作成されるデータには、このような埋め込みは行われません。<br /><br /> また、データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 以前のインスタンスの列に格納するときに、そのデータが長すぎて列に収まりきらない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はデータを右側から切り捨てます。<br /><br /> 注: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーはへの接続をサポートして[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]6.5 およびそれ以前です。|  
|SQL_CHAR (切り捨て)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 以前のインスタンスに接続し、データを SQL_CHAR 型の列に格納するときに、そのデータが長すぎて列に収まりきらない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では警告を通知せずにデータを右側から切り捨てます。<br /><br /> 注: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーはへの接続をサポートして[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]6.5 およびそれ以前です。|  
|SQL_CHAR (NULL 値を許容)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 以前のインスタンスに接続していて、SQL_CHAR 型の列で NULL 値が許容される場合、データ ソースに格納されているデータには空白が埋め込まれません。 このような列からデータを取得するとき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーが、右側の空白を埋め込みます。 ただし、連結など、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により実行される操作で作成されるデータには、このような埋め込みは行われません。<br /><br /> 注: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーはへの接続をサポートして[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]6.5 およびそれ以前です。|  
|SQL_LONGVARBINARY、SQL_LONGVARCHAR、SQL_WLONGVARCHAR|インスタンスに接続しているときに、SQL_LONGVARBINARY、SQL_LONGVARCHAR、SQL_WLONGVARCHAR データ型の列 (WHERE 句を使用) に影響を与える複数の行の更新プログラムが完全にサポートされて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]6 *。x*およびそれ以降。 インスタンスに接続しているときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]4.2*x*、S1000 エラー、"部分的な挿入/更新します。 text または image 列の挿入または更新に失敗しました。" が返されます。<br /><br /> 注: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーはへの接続をサポートして[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]6.5 およびそれ以前です。|  
|文字列関数パラメーター|*string_exp* SQL_CHAR または SQL_VARCHAR データという機能があります。 文字列にパラメーターが入力されます。 SQL_LONG_VARCHAR データ型はサポートされません。 *カウント*パラメーター SQL_CHAR、SQL_VARCHAR データ型は、最大長は 8,000 文字に制限されているためにする 8,000 以下にする必要があります。|  
|時刻リテラル|Sql_timestamp 型の列に格納されているときの時刻リテラル ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータ型**datetime**または**smalldatetime**)、1900 年 1 月 1 日の日付値になります。|  
|**timestamp**|NULL 値だけを手動で挿入されることができます、**タイムスタンプ**列です。 ただし、ため**タイムスタンプ**列はによって自動的に更新[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]NULL 値が上書きされます。|  
|**tinyint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Tinyint**データ型は符号付きではありません。 A **tinyint**列は既定では SQL_C_UTINYINT データ型の変数にバインドします。|  
|別名データ型|インスタンスに接続しているときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]4.2*x*、ODBC ドライバーが、列の null 値許容属性で明示的に宣言されていない列の定義に NULL を追加します。 したがって、別名データ型の定義に格納されている NULL 値の許容属性は無視されます。<br /><br /> インスタンスに接続しているときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]4.2*x*の基本のデータが含まれている別名データ型を持つ列が入力**char**または**バイナリ**し null 値許容属性がありません宣言されているデータ型として作成された**varchar**または**varbinary**です。 [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)、 [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md)、および[SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md)戻り値として SQL_VARCHAR または SQL_VARBINARY データ、これらの列を入力します。 これらの列から取得するデータには、埋め込みは行われません。<br /><br /> 注: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーはへの接続をサポートして[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]6.5 およびそれ以前です。|  
|LONG データ型|*実行時データ*パラメーターは、SQL_LONGVARBINARY、SQL_LONGVARCHAR データ型の両方を制限します。|  
|大きな値型|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは公開**varchar (max)**、 **varbinary (max)**、および**nvarchar (max)** 型として SQL_VARCHAR、SQL_VARBINARY、および sql _WVARCHAR (それぞれ) Api を受け入れるか、ODBC SQL データ型を返します。|  
|ユーザー定義型 (UDT)|UDT 列は SQL_SS_UDT としてマップされます。 SQL ステートメントで、UDT の ToString() メソッドまたは ToXMLString() メソッドを使用するか、CAST/CONVERT 関数を使用して UDT 列を明示的に別の型にマップする場合、結果セット内の列の型には変換された列の実際の型が反映されます。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、UDT 列へのバイナリとしてのみバインドできます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされるのは、SQL_SS_UDT データ型と SQL_C_BINARY データ型の間の変換のみです。|  
|XML|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、XML を Unicode テキストに自動的に変換します。 XML 型は SQL_SS_XML としてマップされます。|  
  
## <a name="see-also"></a>参照  
 [結果の処理&#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
