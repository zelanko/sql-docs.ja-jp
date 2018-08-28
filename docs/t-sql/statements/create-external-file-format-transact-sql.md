---
title: CREATE EXTERNAL FILE FORMAT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 2/20/2018
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL FILE FORMAT
- CREATE_EXTERNAL_FILE_FORMAT
dev_langs:
- TSQL
helpviewer_keywords:
- External
- External, file format
- PolyBase, external file format
ms.assetid: abd5ec8c-1a0e-4d38-a374-8ce3401bc60c
caps.latest.revision: 25
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5c316c7a1e2e2913c5f0b4ce2e2bb4f63a2f5246
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43084310"
---
# <a name="create-external-file-format-transact-sql"></a>外部のファイルの形式 (TRANSACT-SQL) を作成します。
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Hadoop、Azure Blob Storage、または Azure Data Lake Store に格納される外部データを定義する外部ファイル形式オブジェクトを作成します。 外部ファイル形式の作成は、外部テーブルを作成するための前提条件です。 外部ファイル形式を作成することで、外部テーブルによって参照されるデータの実際のレイアウトを指定します。  
  
 PolyBase では、次のファイル形式がサポートされています。
  
-   区切りテキスト  
  
-   Hive RCFile  
  
-   ハイブの ORC
  
-   Parquet  
  
外部テーブルの作成については、「[CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)」をご覧ください。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文
  
```
-- Create an external file format for PARQUET files.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = PARQUET  
     [ , DATA_COMPRESSION = {  
        'org.apache.hadoop.io.compress.SnappyCodec'  
      | 'org.apache.hadoop.io.compress.GzipCodec'      }  
    ]);  
  
--Create an external file format for ORC files.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = ORC  
     [ , DATA_COMPRESSION = {  
        'org.apache.hadoop.io.compress.SnappyCodec'  
      | 'org.apache.hadoop.io.compress.DefaultCodec'      }  
    ]);  
  
--Create an external file format for RCFILE.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = RCFILE,  
    SERDE_METHOD = {  
        'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe'  
      | 'org.apache.hadoop.hive.serde2.columnar.ColumnarSerDe'  
    }  
    [ , DATA_COMPRESSION = 'org.apache.hadoop.io.compress.DefaultCodec' ]);  
  
--Create an external file format for DELIMITED TEXT files.  
CREATE EXTERNAL FILE FORMAT file_format_name  
WITH (  
    FORMAT_TYPE = DELIMITEDTEXT  
    [ , FORMAT_OPTIONS ( <format_options> [ ,...n  ] ) ]  
    [ , DATA_COMPRESSION = {  
           'org.apache.hadoop.io.compress.GzipCodec'  
         | 'org.apache.hadoop.io.compress.DefaultCodec'  
        }  
     ]);  
  
<format_options> ::=  
{  
    FIELD_TERMINATOR = field_terminator  
    | STRING_DELIMITER = string_delimiter 
    | First_Row = integer -- ONLY AVAILABLE SQL DW
    | DATE_FORMAT = datetime_format  
    | USE_TYPE_DEFAULT = { TRUE | FALSE } 
    | Encoding = {'UTF8' | 'UTF16'} 
}  
```  
  
## <a name="arguments"></a>引数  
 *file_format_name*  
 外部のファイル形式の名前を指定します。
  
 FORMAT_TYPE = [ PARQUET | ORC | RCFILE | PARQUET] Specifies the format of the external data.
  
   -   PARQUET は、Parquet 形式を指定します。
  
   -   ORC  
   最適化行多桁式 (ORC) 形式を指定します。 このオプションでは、Hive の外部の Hadoop クラスター上 0.11 以降のバージョンが必要です。 Hadoop, ORC ファイルの形式には、圧縮と RCFILE ファイルの形式よりもパフォーマンスの向上が用意されています。

   -   RCFILE (SERDE_METHOD = *SERDE_method* との組み合わせ): レコード単票形式ファイル形式 (RcFile)。 このオプションでは、ハイブのシリアライザーとデシリアライザー (SerDe) メソッドを指定する必要があります。 この要件は、rc 版のファイルにクエリを使用して hadoop Hive と HiveQL を使用する場合は同じです。 SerDe メソッドは大文字と小文字の区別があることに注意してください。

   PolyBase をサポートする 2 つの SerDe メソッドで RCFile を指定する例です。

    -   FORMAT_TYPE RCFILE、SERDE_METHOD の = = 'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe'

    -   FORMAT_TYPE RCFILE、SERDE_METHOD の = = 'org.apache.hadoop.hive.serde2.columnar.ColumnarSerDe'

   -   DELIMITEDTEXT: フィールド ターミネータとも呼ばれる、列の区切り記号付きのテキスト形式を指定します。
  
 FIELD_TERMINATOR = *field_terminator*  
区切られたテキスト ファイルにのみ適用されます。 フィールド ターミネータは、テキスト区切りファイルでの各フィールド (列) の終了を示す 1 つ以上の文字を指定します。 既定では、パイプ文字 ꞌ|ꞌ です。 サポートが保証されるよう、1 つまたは複数の Ascii 文字を使うことをお勧めします。
  
  
 例 :  
  
-   FIELD_TERMINATOR = ' |'  
  
-   FIELD_TERMINATOR = ' '  
  
-   FIELD_TERMINATOR ꞌ\tꞌ を =  
  
-   FIELD_TERMINATOR = ' ~ | ~'  
  
 STRING_DELIMITER = *string_delimiter*  
テキスト区切りのファイルには、文字列型のデータのフィールド ターミネータを指定します。 文字列の区切り記号の長さの 1 つ以上の文字は、単一引用符で囲まれています。 既定では、空の文字列""です。 サポートが保証されるよう、1 つまたは複数の Ascii 文字を使うことをお勧めします。
 
  
 例 :  

-   STRING_DELIMITER = '"'

-   STRING_DELIMITER = '0x22' -- 二重引用符の十六進値
  
-   STRING_DELIMITER = ' *'  
  
-   STRING_DELIMITER Ꞌ、Ꞌ を =  
  
-   STRING_DELIMITER = '0x7E0x7E' -- 2 個のチルダ (~~)
 
 FIRST_ROW = *First_row_int*  
PolyBase の読み込みの間にすべてのファイルで最初に読み取る行番号を指定します。 このパラメーターで指定できる値は 1 ～ 15 です。 2 に設定すると、データが読み込まれるときに、すべてのファイルの最初の行 (ヘッダー行) がスキップされます。 行は、行ターミネータ (/r/n、/r、/n) の存在に基づいてスキップされます。 このオプションをエクスポートに使うと、行がデータに追加されて、データ損失なしにファイルを読み取ることができます。 2 より大きい値に設定する場合は、エクスポートされる最初の行は外部テーブルの列名です。

 DATE\_FORMAT = *datetime_format*  
区切りテキスト ファイルに出現する可能性のあるすべての日付データと時刻データのカスタム形式を指定します。 ソース ファイルで既定の datetime 形式が使われている場合は、このオプションは必要ありません。 指定できるカスタム datetime 形式は、ファイルごとに 1 つだけです。 1 つのファイルに複数のカスタム datetime 形式を指定することはできません。 ただし、各形式が外部テーブル定義でそれぞれのデータ型の既定の形式になっている場合は、複数の datetime 形式を使うことができます。

PolyBase では、カスタム日付形式はデータのインポートに対してのみ使われます。 外部ファイルへのデータの書き込みには、カスタム書式は使われません。

 DATE_FORMAT が指定されていないか、空の文字列の場合、PolyBase は次の既定の形式を使います。
  
-   DateTime: ' - yyyy-mm-dd HH:mm:ss'  
  
-   SmallDateTime: ' - yyyy-mm-dd HH:mm'  
  
-   日付 ］: ' - yyyy-mm-dd '  
  
-   DateTime2: ' - yyyy-mm-dd HH:mm:ss'  
  
-   DateTimeOffset: ' - yyyy-mm-dd HH:mm:ss'  
  
-   時刻: ' HH:mm:ss'  
  
**日付形式の例**を次の表に示します。
  
テーブルに関する注意:  
  
-   年、月、および日の形式と注文のさまざまなことができます。 表では、**ymd** 形式のみを示します。 月は、1 または 2 桁の数字、または 3 つの文字で指定できます。 日は、1 または 2 桁の数字で指定できます。 年は、2 または 4 桁の数字で指定できます。
  
-   ミリ秒 (fffffff) は、必須ではありません。
  
-   AM/PM (tt) は、必須ではありません。 既定では、AM は。
  
|日付型|例|[説明]|  
|---------------|-------------|-----------------|  
|DateTime|DATE_FORMAT = 'yyyy-mm-dd HH:mm:ss.fff'|年、月、日に加えて、この日付形式には、00-24 の時、00-59 の分、00-59 の秒、3 桁のミリ秒が含まれます。|  
|DateTime|DATE_FORMAT = 'yyyy-mm-dd hh:mm:ss.ffftt'|年、月、日に加えて、この日付形式には、00-12 の時、00-59 の分、00-59 の秒、3 桁のミリ秒、および AM/am/PM/pm が含まれます。 |  
|SmallDateTime|DATE_FORMAT = ' - yyyy-mm-dd HH:mm'|年、月、日に加えて、この日付形式には、00-23 の時、00-59 の分が含まれます。|  
|SmallDateTime|DATE_FORMAT = 'yyyy-mm-dd hh:mmtt'|年、月、日に加えて、この日付形式には、00-11 の時、00-59 の分、AM/am/PM/pm が含まれ、秒は含まれません。|  
|date|DATE_FORMAT = ' yyyy MM dd'|年、月、および日です。 Time 要素が含まれていない場合です。|  
|date|DATE_FORMAT = ' yyyy-MMM-dd'|年、月、および日です。 月を指定するには 3 つの M のいずれか、または年 1 月、年 2 月、年 3 月、年 4 月、月、6 月 6 日、年 7 月、年 8 月、年 9 月、年 10 月、年 11 月、または年 12 月の文字列は入力の値です。|  
|DateTime2|DATE_FORMAT = 'yyyy-mm-dd HH:mm:ss.fffffff'|年、月、日に加えて、この日付形式には、00-23 の時、00-59 の分、00-59 の秒、7 桁のミリ秒が含まれます。|  
|datetime2|DATE_FORMAT = 'yyyy-mm-dd hh:mm:ss.ffffffftt'|年、月、日に加えて、この日付形式には、00-11 の時、00-59 の分、00-59 の秒、7 桁のミリ秒、および AM/am/PM/pm が含まれます。|  
|DateTimeOffset|DATE_FORMAT = 'yyyy-mm-dd HH:mm:ss.fffffff zzz'|年、月、日に加えて、この日付形式には、00-23 の時、00-59 の分、00-59 の秒、7 桁のミリ秒、および `{+&#124;-}HH:ss` として入力ファイルに格納するタイムゾーンのオフセットが含まれます。 たとえば、Los Angeles 後 (夏時間) なしの節約は、UTC、-08 の値の背後にある、8 時間: 00 入力ファイルでは、ロサンゼルスのタイム ゾーンを指定します。|  
|DateTimeOffset|DATE_FORMAT = 'yyyy-mm-dd hh:mm:ss.ffffffftt zzz'|年、月、日に加えて、この日付形式には、00-11 の時、00-59 の分、00-59 の秒、7 桁のミリ秒、AM/am/PM/pm、およびタイムゾーンのオフセットが含まれます。 前の行の説明を参照してください。|  
|Time|DATE_FORMAT = 'HH:mm:ss'|00 ～ 23 ののみ、日付の値はありません時間、00 ～ 59 分、および 00 ～ 59 秒。|  
  
 すべてには、日付の形式がサポートされています。
  
|DATETIME|smalldatetime|日付|datetime2|datetimeoffset|  
|--------------|-------------------|----------|---------------|--------------------|  
|[M [M]M-[d] d-[yy] yy HH:mm:ss [.fff]|[M [M]M-[d] d-[yy] yy HH:mm [: 00]|[M [M]M-[d] d-[yy] yy|[M [M]M-[d] d-[yy] yy HH:mm:ss [.fffffff]|[M [M]M-[d] d-[yy] yy HH:mm:ss [.fffffff] zzz|  
|[M [M]M-[d] d-[yy] yy hh:mm:ss [.fff] [tt]|[M [M]M-[d] d-[yy] yy hh:mm [: 00] [tt]||[M [M]M-[d] d-[yy] yy hh:mm:ss [.fffffff] [tt]|[M [M]M-[d] d-[yy] yy hh:mm:ss [.fffffff] [tt] zzz|  
|[M [M]M [yy] yy-[d]-d HH:mm:ss [.fff]|[M [M]M [yy] yy-[d]-d HH:mm [: 00]|[M [M]M-[yy] yy-[d] d|[M [M]M [yy] yy-[d]-d HH:mm:ss [.fffffff]|[M [M]M [yy] yy-[d]-d HH:mm:ss [.fffffff] zzz|  
|[M [M]M-[yy] yy-[d] d hh:mm:ss [.fff] [tt]|[M [M]M-[yy] yy-[d] d hh:mm [: 00] [tt]||[M [M]M-[yy] yy-[d] d hh:mm:ss [.fffffff] [tt]|[M [M]M-[yy] yy-[d] d hh:mm:ss [.fffffff] [tt] zzz|  
|[yy] yy M [M] M-[d]-d HH:mm:ss [.fff]|[yy] yy M [M] M-[d]-d HH:mm [: 00]|[yy] yy-[M [M] d M-[d]|[yy] yy M [M] M-[d]-d HH:mm:ss [.fffffff]|[yy] yy - M [M] M-[d] d HH:mm:ss [.fffffff] zzz|  
|[yy] yy - M [M] M-[d] d hh:mm:ss [.fff] [tt]|[yy] yy - M [M] M-[d] d hh:mm [: 00] [tt]||[yy] yy - M [M] M-[d] d hh:mm:ss [.fffffff] [tt]|[yy] yy - M [M] M-[d] d hh:mm:ss [.fffffff] [tt] zzz|  
|[yy] yy-[d] d - M [M] M HH:mm:ss [.fff]|[yy] yy-[d] d - M [M] M HH:mm [: 00]|[yy] yy - d を [d]-[M] M|[yy] yy-[d] d - M [M] M HH:mm:ss [.fffffff]|[yy] yy-[d] d - M [M] M HH:mm:ss [.fffffff] zzz|  
|[yy] yy-[d] d - M [M] M hh:mm:ss [.fff] [tt]|[yy] yy-[d] d - M [M] M hh:mm [: 00] [tt]||[yy] yy-[d] d - M [M] M hh:mm:ss [.fffffff] [tt]|[yy] yy-[d] d - M [M] M hh:mm:ss [.fffffff] [tt] zzz|  
|[d] d - M [M] M-[yy] yy HH:mm:ss [.fff]|[d] d - M [M] M-[yy] yy HH:mm [: 00]|[d] d - M [M] M-[yy] yy|[d] d - M [M] M-[yy] yy HH:mm:ss [.fffffff]|[d] d - M [M] M-[yy] yy HH:mm:ss [.fffffff] zzz|  
|[d] d - M [M] M-[yy] yy hh:mm:ss [.fff] [tt]|[d] d - M [M] M-[yy] yy hh:mm [: 00] [tt]||[d] d - M [M] M-[yy] yy hh:mm:ss [.fffffff] [tt]|[d] d - M [M] M-[yy] yy hh:mm:ss [.fffffff] [tt] zzz|  
|[d] d-[yy] yy - M [M] M HH:mm:ss [.fff]|[d] d-[yy] yy - M [M] M HH:mm [: 00]|[d] d-[yy] yy - M [M] M|[d] d-[yy] yy - M [M] M HH:mm:ss [.fffffff]|[d] d-[yy] yy - M [M] M HH:mm:ss [.fffffff] zzz|  
|[d] d-[yy] yy - M [M] M hh:mm:ss [.fff] [tt]|[d] d-[yy] yy - M [M] M hh:mm [: 00] [tt]||[d] d-[yy] yy - M [M] M hh:mm:ss [.fffffff] [tt]|[d] d-[yy] yy - M [M] M hh:mm:ss [.fffffff] [tt] zzz|  
  
 詳細:  
  
-   月、日、年の値を区切るには、"–"、"/"、"." を使うことができます。 わかりやすくするために、テーブルは、'-' の区切りを使用します。
  
-   月をテキストとして指定するには、3 つ以上の文字を使います。 1 つまたは 2 つの文字で表された月は、数値として解釈されます。
  
-   時刻の値を区切るには、":" 記号を使います。
  
-   角かっこで囲まれた文字では、オプションです。
  
-   文字 'tt' [AM| を指定します。PM|am|pm] です。 AM 既定値です。 'Tt' を指定すると、時間の値 (hh) は、0 ～ 12 の範囲でなければなりません。
  
-   現在のタイム ゾーン形式で、システムのタイム ゾーン オフセットを指定する文字 'zzz' {+ |-} HH:ss] です。
  
 USE_TYPE_DEFAULT = { TRUE | **FALSE** }  
 PolyBase がテキスト ファイルからデータを取得するときに、区切られたテキスト ファイル内の不足値を処理する方法を指定します。
  
 TRUE  
 テキスト ファイルからデータを取得するときに、外部テーブルの定義に対応する列のデータ型の既定値を使用して、各の不足している値を格納します。 たとえばを使用して不足値に置き換えます。  
  
-   列が数値型の列として定義されている場合は、0 を返します。
  
-   空の文字列""、列が文字列型の列である場合。
  
-   列が date 列の場合は 1900-01-01 です。
  
 FALSE  
 NULL としては、すべての不足値を格納します。 区切りテキスト ファイルで単語 NULL を使って格納されている NULL 値は、文字列 "NULL" としてインポートされます。
  
   Encoding = {'UTF8' | 'UTF16'}  
 Azure SQL Data Warehouse では、PolyBase は UTF8 および UTF16-LE でエンコードされた区切りテキスト ファイルを読み取ることができます。 SQL Server と PDW では、PolyBase は UTF16 でエンコードされたファイルの読み取りをサポートしていません。
  
 DATA_COMPRESSION = *data_compression_method*  
 外部データのデータ圧縮方法を指定します。 DATA_COMPRESSION を指定しない場合の既定値は、圧縮されていないデータです。
 正しく動作するためには、Gzip で圧縮されたファイルの拡張子が ".gz" である必要があります。
 
 DELIMITEDTEXT 書式の種類には、これらのメソッドの圧縮がサポートされています。
  
-   データ圧縮 = 'org.apache.hadoop.io.compress.DefaultCodec'
  
-   データ圧縮 = 'org.apache.hadoop.io.compress.GzipCodec'

 RCFILE 書式の種類には、この圧縮メソッドがサポートされています。
  
-   データ圧縮 = 'org.apache.hadoop.io.compress.DefaultCodec'
  
 ORC ファイル形式の種類には、これらのメソッドの圧縮がサポートされています。
  
-   データ圧縮 = 'org.apache.hadoop.io.compress.DefaultCodec'
  
-   データ圧縮 = 'org.apache.hadoop.io.compress.SnappyCodec'
  
 PARQUET ファイル形式の種類では、次の圧縮方法がサポートされています。
  
-   データ圧縮 = 'org.apache.hadoop.io.compress.GzipCodec'
  
-   データ圧縮 = 'org.apache.hadoop.io.compress.SnappyCodec'
  
## <a name="permissions"></a>アクセス許可  
 任意の外部ファイル形式の ALTER 権限が必要です。
  
## <a name="general-remarks"></a>全般的な解説
 外部ファイルの形式は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ではデータベース スコープです。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ではサーバー スコープです。  
  
 形式オプションはすべてオプションと、区切られたテキスト ファイルにのみ適用されます。  
  
 いずれかの圧縮形式でデータが格納されていると、PolyBase は最初にデータの圧縮を解除してから、データ レコードを返します。
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項
  
 区切りテキスト ファイルの行区切り記号は、Hadoop の LineRecordReader でサポートされている必要があります。 つまり、"\r"、"'\n"、"\r\n" のいずれかでなければなりません。 これらの区切り記号はユーザー構成可能ではありません。
  
 サポートされる SerDe メソッドと RCFile の組み合わせ、およびサポートされるデータ圧縮方法は、この記事で前に示しました。 すべての組み合わせがサポートされます。
  
 PolyBase の同時実行クエリの最大数は、32 です。 32 の同時実行クエリが実行しているときに、各クエリは、外部のファイルの場所から 33,000 ファイルの最大を読み取ることができます。 ルート フォルダーと各サブフォルダーは、また、ファイルとしてカウントされます。 同時実行の程度が 32 未満である場合は、外部のファイルの場所は 33,000 複数のファイルを含めることができます。
  
 制限のため、外部テーブル内のファイルの数を 30,000 より小さいファイルを保存するルートと、外部のファイルの場所のサブフォルダーをお勧めします。 また、ルート ディレクトリの下のサブフォルダーの数を小さい数にすることをお勧めします。 参照されているファイルが多すぎる場合、Java 仮想マシンのメモリ不足例外が発生する可能性があります。
  
  PolyBase で Hadoop または Azure Blob Storage にデータをエクスポートするときは、データだけがエクスポートされて、CREATE EXTERNAL TABLE コマンドで定義されている列名 (メタデータ) はエクスポートされません。

## <a name="locking"></a>ロック  
 外部のファイル形式のオブジェクトには、共有ロックを取得します。
  
## <a name="performance"></a>[パフォーマンス]
 常に圧縮されたファイルを使用してには、バランスを取るようにして、データの圧縮 CPU 使用率の向上と、外部データ ソースと SQL Server の間でのデータを転送する間あります。
  
 Gzip で圧縮されたテキスト ファイルは分割可能ではありません。 Gzip で圧縮されたテキスト ファイルのパフォーマンスを向上させるには、複数のファイルを生成し、そのすべてを外部データ ソースの同じディレクトリに格納することをお勧めします。 このようなファイル構造にすると、PolyBase は、複数のリーダー プロセスと圧縮解除プロセスを使って、より速くデータを圧縮解除できます。 圧縮されたファイルの理想的な数は、計算ノードあたりのデータ リーダー プロセスの最大数です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] の現在のリリースでは、データ リーダー プロセスの最大数はノードあたり 8 個です。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] では、ノードごとのデータ リーダー プロセスの最大数は SLO によって変化します。 詳しくは、「[Azure SQL Data Warehouse loading patterns and strategies](https://blogs.msdn.microsoft.com/sqlcat/2016/02/06/azure-sql-data-warehouse-loading-patterns-and-strategies/)」(Azure SQL Data Warehouse の読み込みパターンと戦略) をご覧ください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-create-a-delimitedtext-external-file-format"></a>A. DELIMITEDTEXT 外部ファイル形式を作成する  
 この例では、テキスト区切りファイル用に *textdelimited1* という名前の外部ファイル形式を作成します。 FORMAT\_OPTIONS のオプション リストでは、ファイルのフィールドをパイプ文字 "|" を使って区切ることが指定されています。 テキスト ファイルは Gzip コーデックで圧縮されます。 DATA\_COMPRESSION を指定しないと、テキスト ファイルは圧縮されません。
  
 区切りテキスト ファイルの場合、データ圧縮方法は、既定のコーデック "org.apache.hadoop.io.compress.DefaultCodec" または Gzip コーデック "org.apache.hadoop.io.compress.GzipCodec" です。
  
```  
CREATE EXTERNAL FILE FORMAT textdelimited1  
WITH (  
    FORMAT_TYPE = DELIMITEDTEXT,  
    FORMAT_OPTIONS (  
        FIELD_TERMINATOR = '|',  
        DATE_FORMAT = 'MM/dd/yyyy' ),  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.GzipCodec'
);  
```  
  
### <a name="b-create-an-rcfile-external-file-format"></a>B. RCFile 外部ファイル形式を作成する  
 この例では、シリアル化/逆シリアル化方法として org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe を使う RCFile の外部ファイル形式を作成します。 データの圧縮方法の既定のコーデックを使用することも指定します。 DATA_COMPRESSION を指定しない場合の既定の設定は非圧縮です。
  
```  
CREATE EXTERNAL FILE FORMAT rcfile1  
WITH (  
    FORMAT_TYPE = RCFILE,  
    SERDE_METHOD = 'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe',  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.DefaultCodec'  
);  
```  
  
### <a name="c-create-an-orc-external-file-format"></a>C. ORC の外部のファイル形式を作成します。  
 この例では、org.apache.io.compress.SnappyCodec データ圧縮方法でデータを圧縮する ORC ファイルの外部ファイル形式を作成します。 DATA_COMPRESSION を指定しない場合の既定の設定は非圧縮です。
  
```  
CREATE EXTERNAL FILE FORMAT orcfile1  
WITH (  
    FORMAT_TYPE = ORC,  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.SnappyCodec'  
);  
```  
  
### <a name="d-create-a-parquet-external-file-format"></a>D. PARQUET 外部ファイル形式を作成する  
 この例では、org.apache.io.compress.SnappyCodec データ圧縮方法でデータを圧縮する Parquet ファイルの外部ファイル形式を作成します。 DATA_COMPRESSION を指定しない場合の既定の設定は非圧縮です。  
  
```  
CREATE EXTERNAL FILE FORMAT parquetfile1  
WITH (  
    FORMAT_TYPE = PARQUET,  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.SnappyCodec'  
);  
```  
### <a name="e-create-a-delimited-text-file-skipping-header-row-azure-sql-dw-only"></a>E. 区切りテキスト ファイルのスキップ ヘッダー行を作成する (Azure SQL DW のみ)
 この例では、ヘッダー行が 1 つの CSV ファイルの外部ファイル形式を作成します。 
  
```  
CREATE EXTERNAL FILE FORMAT skipHeader_CSV
WITH (FORMAT_TYPE = DELIMITEDTEXT,
      FORMAT_OPTIONS(
          FIELD_TERMINATOR = ',',
          STRING_DELIMITER = '"',
          FIRST_ROW = 2, 
          USE_TYPE_DEFAULT = True)
)
```   

## <a name="see-also"></a>参照
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)   
 [CREATE EXTERNAL TABLE AS SELECT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
 [CREATE TABLE AS SELECT &#40;Azure SQL Data Warehouse&#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)   
 [sys.external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)  
