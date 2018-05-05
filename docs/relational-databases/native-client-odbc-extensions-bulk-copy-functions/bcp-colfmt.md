---
title: bcp_colfmt |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_colfmt
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_colfmt function
ms.assetid: 5c3b6299-80c7-4e84-8e69-4ff33009548e
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: de5e429a0b2038064bfde3cf4835d4f8edd4beff
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="bcpcolfmt"></a>bcp_colfmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ユーザー ファイルのデータのコピー元またはコピー先の形式を指定します。 ソースの形式として使用すると**bcp_colfmt**への一括コピーでデータのソースとして使用される既存のデータ ファイルの形式を指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。 指定された列の形式を使用してデータ ファイルを作成する、ターゲットの形式として使用されるときに**bcp_colfmt**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_colfmt (  
        HDBC hdbc,  
        INT idxUserDataCol,  
        BYTE eUserDataType,  
        INT cbIndicator,  
        DBINT cbUserData,  
        LPCBYTE pUserDataTerm,  
        INT cbUserDataTerm,  
        INT idxServerCol);  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *idxUserDataCol*  
 ユーザー データ ファイルの、形式が指定される列の序数です。 最初の列は 1 です。  
  
 *eUserDataType*  
 ユーザー ファイル内にある列のデータ型です。 データベース テーブル内の対応する列のデータ型と異なる場合 (*idxServerColumn*)、一括コピーが可能であれば、データを変換します。  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SQLXML、SQLUDT データ型のトークンのサポートが導入されました、 *eUserDataType*パラメーター。  
  
 *EUserDataType*パラメーターは列挙型、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sqlncli.h 内のデータ型のトークン、されません、ODBC C データ型の列挙子。 たとえば、文字の文字列では、ODBC を指定できます SQL_C_CHAR の型を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-特定の種類 SQLCHARACTER です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型に対して既定のデータ表現を指定するには、このパラメーターに 0 を設定します。  
  
 一括コピーの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をファイルと*eUserDataType* SQLDECIMAL または SQLNUMERIC は。  
  
-   基になる列がない場合**10 進**または**数値**既定の有効桁数と小数点以下桁数が使用されます。  
  
-   ソース列がある場合**decimal**または**数値**、有効桁数と基になる列の小数点以下桁数を使用します。  
  
 *cbIndicator*  
 列データ内にある長さのインジケーターや NULL インジケーターのバイト単位の長さです。 インジケーターの長さの有効値は、0 (インジケーターを使用しない場合)、1、2、4、または 8 です。  
  
 一括コピーのインジケーターの既定の使用方法を指定するには、このパラメーターに SQL_VARLEN_DATA を設定します。  
  
 インジケーターは、メモリ内ではすべてのデータの直前に、データ ファイル内ではインジケーターを適用するデータの直前に配置します。  
  
 複数の方法 (インジケーターと列の最大長、インジケーターとターミネータ シーケンスなど) を使用してデータ ファイルの列長を指定すると、一括コピーではコピーするデータの量が最も少なくなる方法が使用されます。  
  
 ユーザーの操作でデータの形式が調整されずに一括コピーで生成されたデータ ファイルには、列データの長さが異なる場合や、列の値に NULL が許容される場合にインジケーターが含まれます。  
  
 *cbUserData*  
 ユーザー ファイル内にある列データの最大長 (バイト単位)。長さのインジケーターやターミネータの長さは含まれません。  
  
 設定*cbUserData* SQL_NULL_DATA することを示しますデータ ファイルの列のすべての値、または NULL に設定する必要があります。  
  
 設定*cbUserData*を SQL_VARLEN_DATA に示す、システムが各列のデータの長さを決定する必要があります。 これは、列によっては、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からコピーされるデータの前に長さのインジケーターや NULL インジケーターを生成したり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にコピーするデータにインジケーターが必要になる場合があることを意味します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字やバイナリ データ型、 *cbUserData* SQL_VARLEN_DATA、SQL_NULL_DATA、0 または正の値を指定できます。 場合*cbUserData*が sql_varlen_data の場合、システムは存在する場合は、長さのインジケーターやターミネータ シーケンスのいずれかを使用して、データの長さを決定します。 長さのインジケーターとターミネータ シーケンスの両方を指定した場合、一括コピーはコピーするデータ量が少なくなる方法を使用します。 場合*cbUserData*が sql_varlen_data の場合、データ型は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字またはバイナリ型でともない長さのインジケーターとターミネータ シーケンスを指定すると、システム エラー メッセージが返されます。  
  
 場合*cbUserData*が 0 または正の値は、システムが使用*cbUserData*最大データ長として。 ただし、正の値にいる場合、 *cbUserData*長さのインジケーターとターミネータ シーケンスの提供、コピーするデータの量が最も少なくなる方法を使用して、データの長さを決定します。  
  
 *CbUserData*値は、データのバイト数を表します。 文字データが Unicode ワイド文字、正の値で表されている場合*cbUserData*パラメーターの値は、各文字のバイト単位のサイズを乗算する文字の数を表します。  
  
 *pUserDataTerm*  
 列に使用するターミネータ シーケンスです。 このパラメーターは主に文字データ型に対して有効です。これは、他のすべての型は固定長であったり、バイト数を正確に記録するために長さのインジケーターが必要になる (バイナリ データの場合) ためです。  
  
 抽出されるデータが途中で終了されないようにしたり、ユーザー ファイル内のデータが途中で終了していないことを示すには、このパラメーターに NULL を設定します。  
  
 複数の方法 (ターミネータと長さのインジケーター、ターミネータと列の最大長など) を使用してユーザー ファイルの列長を指定すると、一括コピーはコピーするデータの量が最も少なくなる方法を使用します。  
  
 一括コピー API では、必要に応じて Unicode から MBCS への文字変換が実行されます。 このため、ターミネータのバイト文字列とそのバイト文字列の長さの両方を正しく設定するように注意する必要があります。  
  
 *cbUserDataTerm*  
 列に使用するターミネータ シーケンスの長さ (バイト単位)。 データ内にターミネータが存在しないか不要な場合は、この値を 0 に設定します。  
  
 *idxServerCol*  
 データベース テーブルの列の序数位置です。 最初の列の序数は 1 です。 列の序数位置がによって報告された[SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md)です。  
  
 この値が 0 の場合、一括コピーではデータ ファイル内のこの列が無視されます。  
  
## <a name="returns"></a>返します。  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>解説  
 **Bcp_colfmt**関数では、一括コピーのユーザー ファイルの形式を指定することができます。 次に、一括コピーに使用するフォーマットの内容を示します。  
  
-   ユーザー ファイルの列からデータベース列へのマッピング  
  
-   ユーザー ファイルの各列のデータ型  
  
-   各列の省略可能なインジケーターの長さ  
  
-   ユーザー ファイルの各列におけるデータの最大長  
  
-   各列の省略可能なターミネータ バイト シーケンス  
  
-   省略可能なターミネータ バイト シーケンスの長さ  
  
 各呼び出し**bcp_colfmt**ユーザー ファイルの 1 つの列の形式を指定します。 たとえば、5 つの列のユーザー データ ファイル内の 3 つの列の既定の設定を変更するに最初に呼び出す[bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)**(5)**、およびを呼び出す**bcp_colfmt**に 5 回、これらの 3 つを呼び出すカスタム形式を設定します。 残りの 2 つの呼び出しでは、設定*eUserDataType*を 0 に設定し*cbIndicator*、 *cbUserData*、および*cbUserDataTerm* 0、SQL_VARLEN_DATA で、0 それぞれします。 このプロシージャでは、5 つの列すべてをコピーします。それらの列のうち 3 つはカスタマイズされた形式でコピーされ、2 つは既定の形式でコピーされます。  
  
 *CbIndicator*、大きな値の型を示すために 8 の値は有効です。 フィールドにプレフィックスを指定し、そのフィールドに対応する列が新しい max 型である場合、この値は 8 にしか設定できません。 詳細については、「 [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)です。  
  
 **Bcp_columns**呼び出しの前に関数を呼び出す必要があります**bcp_colfmt**です。  
  
 呼び出す必要があります**bcp_colfmt**ユーザー ファイル内の各列に対して 1 回です。  
  
 呼び出す**bcp_colfmt** 1 回以上のユーザー ファイルの任意の列、エラーが発生します。  
  
 ユーザー ファイル内のすべてのデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにコピーする必要はありません。 列をスキップするには、設定、列のデータの形式を指定、 *idxServerCol*パラメーターを 0 にします。 列をスキップする場合でも、その列の型を指定する必要があります。  
  
 [Bcp_writefmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md)関数は、書式指定を永続化に使用できます。  
  
## <a name="bcpcolfmt-support-for-enhanced-date-and-time-features"></a>bcp_colfmt による機能強化された日付と時刻のサポート  
 使用される型については、 *eUserDataType*日付/時刻型のパラメーターを参照してください[強化された日付と時刻型の変更の一括コピー &#40;OLE DB および ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)です。  
  
 詳細については、次を参照してください。[日付と時刻の強化 (&) #40";"ODBC"&"#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
