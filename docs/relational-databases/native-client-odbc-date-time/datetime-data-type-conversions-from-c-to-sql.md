---
title: C から SQL への変換 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC], C to SQL
ms.assetid: 7ac098db-9147-4883-8da9-a58ab24a0d31
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9f8161ea07e394192e972caf4f772d9e7def36e5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301793"
---
# <a name="datetime-data-type-conversions-from-c-to-sql"></a>datetime データ型の C から SQL への変換
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  このトピックでは、C 型から日付/時刻型に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換する際に考慮すべき問題を示します。  
  
 次の表で説明する変換は、クライアントで行われる変換に当てはまります。 サーバーで定義されているパラメーターとは異なるパラメーターに対してクライアントが秒の小数精度を指定している場合、クライアント変換は成功する可能性がありますが **、SQLExecute**または**SQLExecuteDirect**が呼び出されるとサーバーはエラーを返します。 特に、ODBC は秒の小数秒の切り捨てをすべてエラーとして扱いますが[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、動作は丸めになります。たとえば、丸めは **、日付時刻 2(6) から datetime2(2)** に移動すると発生します。 **datetime2(2)** datetime 列の値は 1/300 秒単位に丸められ、smalldatetime 列では、サーバーによって秒が 0 に設定されます。  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
||SQL_TYPE_DATE|SQL_TYPE_TIME|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_SS_TIMSTAMPOFFSET|SQL_CHAR|SQL_WCHAR|  
|SQL_C_DATE|1|-|-|1,6|1,5,6|1,13|1,13|  
|SQL_C_TIME|-|1|1|1,7|1,5,7|1,13|1,13|  
|SQL_C_SS_TIME2|-|1,3|1,10|1,7|1,5,7|1,13|1,13|  
|SQL_C_BINARY(SQL_SS_TIME2_STRUCT)|該当なし|該当なし|1,10,11|該当なし|該当なし|該当なし|該当なし|  
|SQL_C_TYPE_TIMESTAMP|1、2|1,3,4|1,4,10|1,10|1,5,10|1,13|1,13|  
|SQL_C_SS_TIMESTAMPOFFSET|1,2,8|1,3,4,8|1,4,8,10|1,8,10|1,10|1,13|1,13|  
|SQL_C_BINARY(SQL_SS_TIMESTAMPOFFSET_STRUCT)|該当なし|該当なし|該当なし|該当なし|1,10,11|該当なし|該当なし|  
|SQL_C_CHAR/SQL_WCHAR (date)|9|9|9|9,6|9,5,6|該当なし|該当なし|  
|SQL_C_CHAR/SQL_WCHAR (time2)|9|9,3|9,10|9,7,10|9,5,7,10|該当なし|該当なし|  
|SQL_C_CHAR/SQL_WCHAR (datetime)|9,2|9,3,4|9,4,10|9,10|9,5,10|該当なし|該当なし|  
|SQL_C_CHAR/SQL_WCHAR (datetimeoffset)|9,2,8|9,3,4,8|9,4,8,10|9,8,10|9,10|該当なし|該当なし|  
|SQL_C_BINARY(SQL_DATE_STRUCT)|1,11|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|  
|SQL_C_BINARY(SQL_TIME_STRUCT)|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|  
|SQL_C_BINARY(SQL_TIMESTAMP_STRUCT)|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|  
  
## <a name="key-to-symbols"></a>記号の説明  
  
-   **-**: 変換はサポートされていません。 "データ型の属性に関する制限に違反しました" というメッセージで SQLSTATE 07006 の診断レコードが生成されます。  
  
-   **1**: 指定されたデータが有効でない場合、診断レコードが SQLSTATE 22007 とメッセージ "無効な日時形式" で生成されます。  
  
-   **2**: 時刻フィールドがゼロであるか、診断レコードが SQLSTATE 22008 とメッセージ 「分数切り捨て」で生成される必要があります。  
  
-   **3**: 秒の小数は 0 にするか、または SQLSTATE 22008 とメッセージ 「分数切り捨て」で診断レコードが生成される必要があります。  
  
-   **4**: 日付コンポーネントは無視されます。  
  
-   **5**: タイムゾーンはクライアントのタイムゾーン設定に設定されます。  
  
-   **6**: 時刻はゼロに設定されます。  
  
-   **7**: 日付は現在の日付に設定されます。  
  
-   **8**: 時刻はクライアントのタイムゾーンから UTC に変換されます。 この変換中にエラーが発生すると、"Datetime フィールド オーバーフロー" というメッセージで SQLSTATE 22008 の診断レコードが生成されます。  
  
-   **9**: 最初に検出された句読点文字と残りのコンポーネントの有無に応じて、文字列が解析されて、日付、日時、日時オフセット、または時刻値に変換されます。 次に、上の表に示した規則のうち、この処理で検出された変換元の型についての規則に従って、文字列は変換先の型に変換されます。 データの解析中にエラーが検出された場合、"キャストした文字コードが正しくありません" というメッセージで SQLSTATE 22018 の診断レコードが生成されます。 datetime 型および smalldatetime 型のパラメーターでは、年がこれらの型でサポートされる範囲外の場合、"datetime 形式が無効です" というメッセージで SQLSTATE 22007 の診断レコードが生成されます。  
  
     datetimeoffset では、UTC への変換が必要なくても、値は UTC への変換後の範囲内に収まっている必要があります。 TDS とサーバーは datetimeoffset 値の時刻を常に UTC 用に正規化するので、クライアントは、時刻部分が、UTC への変換後にサポートされる範囲内に収まっていることを確認する必要があるためです。 値が、サポートされている UTC の範囲内に収まっていない場合、"datetime 形式が無効です" というメッセージで SQLSTATE 22007 の診断レコードが生成されます。  
  
-   **10**: データ損失を伴う切り捨てが発生した場合、診断レコードが SQLSTATE 22008 と「無効な時刻形式」というメッセージで生成されます。 サーバーが使用する UTC の範囲で表すことができる範囲の外に値がある場合にも、このエラーが発生します。  
  
-   **11**: データのバイト長が SQL タイプで必要な構造体のサイズと等しくない場合、診断レコードが SQLSTATE 22003 とメッセージ "範囲外の数値" で生成されます。  
  
-   **12**: データのバイト長が 4 または 8 の場合、データは未加工の TDS スモール日時または日時形式でサーバーに送信されます。 データのバイト長が SQL_TIMESTAMP_STRUCT のサイズと完全に一致する場合、データは、datetime2 用の TDS 形式に変換されます。  
  
-   **13**: データ損失を伴う切り捨てが発生した場合、診断レコードが SQLSTATE 22001 とメッセージ 「文字列データ、右切り捨て」と生成されます。  
  
     秒の小数の桁数 (スケール) は、次の表に従って、変換先列のサイズから決定されます。  
  
    ||||  
    |-|-|-|  
    |Type|暗黙の小数点以下桁数<br /><br /> 0|暗黙の小数点以下桁数<br /><br /> 1..9|  
    |SQL_C_TYPE_TIMESTAMP|19|21..29|  
  
     ただし、SQL_C_TYPE_TIMESTAMP では、データを損失することなく秒の小数部を 3 桁で表すことができる場合で、かつ、列のサイズが 23 以上である場合、ちょうど 3 桁になるように秒の小数部が生成されます。 この動作により、以前の ODBC ドライバーを使用して開発されたアプリケーションの下位互換性が保証されます。  
  
     テーブルの範囲よりサイズが大きい列の場合は、9 桁と見なされます。 この変換では、秒の小数点以下桁数が 9 桁まで許容されます。これは、ODBC で許容される最大桁数です。  
  
     列サイズ 0 は、ODBC では可変長文字型のサイズが無制限であることを意味します (SQL_C_TYPE_TIMESTAMP の 3 桁ルールが適用されなければ 9 桁)。 固定長文字型の列サイズ 0 を指定すると、エラーになります。  
  
-   **N/A**:[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]既存の動作と以前の動作は維持されます。  
  
## <a name="see-also"></a>参照  
 [日付と時刻 ODBC&#41;&#40;改善](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
