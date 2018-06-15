---
title: SQLBindCol |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-api
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3dce23669637b9fd39e9fa84d37600bae6e64f98
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32944547"
---
# <a name="sqlbindcol"></a>SQLBindCol
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  一般的な規則として使用する場合を検討してください。 **SQLBindCol**データ変換が発生します。 バインドによる変換はクライアント側のプロセスなので、たとえば文字型の列にバインドされた浮動小数点値を取得すると、ドライバーは行をフェッチするときにローカルで浮動小数点型から文字型への変換を行います。 [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT 関数を使用すると、データ変換の負荷をサーバーに移すことができます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスでは、1 回のステートメントの実行に対して複数の結果セット行を返すことができます。 各結果セットは個別にバインドされている必要があります。 複数の結果セットのバインドの詳細については、次を参照してください。 [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)です。  
  
 開発者は、列をバインドできます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-特定の C データ型を使用して、 *TargetType*値**SQL_C_BINARY**です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有の型にバインドされた列は移植できません。 また、定義済みの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有の ODBC C データ型は DB-Library の型定義と一致するので、アプリケーションを移植する DB-Library 開発者はこの特性を利用できます。  
  
 負荷の高い処理は、レポート データの切り捨て、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー。 バインドされるすべてのデータ バッファーのサイズがデータを返すのに十分なサイズであれば、データの切り捨てを回避できます。 文字データの場合、文字列の終了に既定のドライバーの動作を使用するときは、データ バッファーの大きさに文字列ターミネータの領域も含める必要があります。 たとえば、バインディング、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char (5)** 列値がフェッチされるごとに切り捨ての結果を 5 つの文字の配列にします。 同じ列を 6 文字の配列にバインドすると、NULL ターミネータを格納する文字要素が用意されるため、切り捨てを回避できます。 [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)切り捨てることがなく、長い文字やバイナリ データを効率的に取得するために使用できます。  
  
 ユーザーが指定したバッファーが、列の値全体を保持するのに十分でない場合、大きな値データ型の**SQL_SUCCESS_WITH_INFO**が返されると、"文字列データです。右側が切り捨てられました"警告が発行されます。 **StrLen_or_IndPtr**引数が文字数とバイト バッファーに格納されている数を格納します。  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>SQLBindCol による機能強化された日付と時刻のサポート  
 」の説明に従って、日付/時刻型の結果列の値が変換された[SQL から C への変換](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)です。それらに対応する構造体として time と datetimeoffset 列を取得することに注意してください (**SQL_SS_TIME2_STRUCT**と**SQL_SS_TIMESTAMPOFFSET_STRUCT**)、 *TargetType*として指定する必要があります**SQL_C_DEFAULT**または**SQL_C_BINARY**です。  
  
 詳細については、次を参照してください。[日付と時刻の強化 (&) #40";"ODBC"&"#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>SQLBindCol による大きな CLR UDT のサポート  
 **SQLBindCol**大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型 (&) #40";"ODBC"&"#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLBindCol 関数](http://go.microsoft.com/fwlink/?LinkId=59327)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
