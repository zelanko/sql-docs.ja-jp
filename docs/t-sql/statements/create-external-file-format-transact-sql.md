---
title: "外部ファイル形式 (TRANSACT-SQL) を作成します |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ab356583cb69cc6e98bacc2a6e28145887902043
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-external-file-format-transact-sql"></a>外部のファイルの形式 (TRANSACT-SQL) を作成します。
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Hadoop や Azure blob ストレージ、Azure Data Lake Store に格納されている外部データ用 PolyBase 外部ファイル形式の定義を作成します。 PolyBase 外部テーブルを作成するための前提条件は、外部のファイル形式を作成します。 を、外部のファイル形式を作成するには、外部テーブルによって参照されるデータの実際のレイアウトを指定します。  
  
 PolyBase には、これらのファイル形式がサポートされています。  
  
-   区切り記号付きテキスト  
  
-   Hive RCFile  
  
-   ハイブの ORC  
  
-   Parquet  
  
 外部テーブルを作成するを参照してください。 [CREATE EXTERNAL TABLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-external-table-transact-sql.md).  
  
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
    | DATE_FORMAT = datetime_format  
    | USE_TYPE_DEFAULT = { TRUE | FALSE } 
    | Encoding = {'UTF8' | 'UTF16'} 
}  
```  
  
## <a name="arguments"></a>引数  
 *file_format_name*  
 外部のファイル形式の名前を指定します。  
  
 FORMAT_TYPE  
 外部データの形式を指定します。  
  
 PARQUET  
 Parquet 形式を指定します。  
  
 ORC  
 最適化行多桁式 (ORC) 形式を指定します。 このオプションでは、Hive の外部の Hadoop クラスター上 0.11 以降のバージョンが必要です。 Hadoop, ORC ファイルの形式には、圧縮と RCFILE ファイルの形式よりもパフォーマンスの向上が用意されています。  
  
 RCFILE (SERDE_METHOD と組み合わせて = *SERDE_method*)  
 レコードの列のファイルの形式 (RcFile) を指定します。 このオプションでは、ハイブのシリアライザーとデシリアライザー (SerDe) メソッドを指定する必要があります。 この要件は、rc 版のファイルにクエリを使用して hadoop Hive と HiveQL を使用する場合は同じです。 SerDe メソッドは大文字小文字を区別に注意してください。  
  
 PolyBase をサポートする 2 つの SerDe メソッドで RCFile を指定する例です。  
  
-   FORMAT_TYPE RCFILE、SERDE_METHOD の = = 'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe'  
  
-   FORMAT_TYPE RCFILE、SERDE_METHOD の = = 'org.apache.hadoop.hive.serde2.columnar.ColumnarSerDe'  
  
 DELIMITEDTEXT  
 フィールド ターミネータとも呼ばれる、列の区切り記号をテキスト形式を指定します。  
  
 FIELD_TERMINATOR = *field_terminator*  
 区切られたテキスト ファイルにのみ適用されます。 これにより、各フィールド (列) の末尾を示す 1 つ以上の文字がテキストで区切られたファイルに指定されます。 既定では、パイプ文字 ꞌ|ꞌ です。 保証されたサポートについては、1 つまたは複数の ascii 文字を使用するお勧めします。
  
  
 例 :  
  
-   FIELD_TERMINATOR = ' |'  
  
-   FIELD_TERMINATOR = ' '  
  
-   FIELD_TERMINATOR ꞌ\tꞌ を =  
  
-   FIELD_TERMINATOR = ' ~ | ~'  
  
 STRING_DELIMITER = *string_delimiter*  
 テキスト区切りのファイルには、文字列型のデータのフィールド ターミネータを指定します。 文字列の区切り記号の長さの 1 つ以上の文字は、単一引用符で囲まれています。 既定では、空の文字列""です。 保証されたサポートについては、1 つまたは複数の ascii 文字を使用するお勧めします。
 
  
 例 :  

-   STRING_DELIMITER = '"'

-   STRING_DELIMITER '0x22'--二重引用符の 16 進数を =
  
-   STRING_DELIMITER = ' *'  
  
-   STRING_DELIMITER Ꞌ、Ꞌ を =  
  
-   STRING_DELIMITER = '0x7E0x7E'--2 tildas (例: ~ ~)
  
 DATE_FORMAT = *datetime_format*  
 区切られたテキスト ファイルに記述するすべての日付と時刻のデータのカスタム書式を指定します。 ソース ファイルには、datefime の既定の形式が使用されている場合は、このオプションは必要はありません。 1 つだけのカスタム日付/時刻形式は、ファイルあたり許可します。 ファイルごとの複数のカスタム日付/時刻形式を指定することはできません。 ただし、それぞれが、外部テーブルの定義のそれぞれのデータ型の既定の形式である場合は、複数の datetime 形式を使用できます。
 
 
PolyBase では、データをインポートするため、カスタムの日付の書式のみ使用します。 外部ファイルにデータを書き込むためのカスタム書式指定は使用しません。

 DATE_FORMAT が指定されていないか、空の文字列、ときに、PolyBase は次の既定の形式を使用します。  
  
-   DateTime: ' - yyyy-mm-dd HH:mm:ss'  
  
-   SmallDateTime: ' - yyyy-mm-dd HH:mm'  
  
-   日付 ］: ' - yyyy-mm-dd '  
  
-   DateTime2: ' - yyyy-mm-dd HH:mm:ss'  
  
-   DateTimeOffset: ' - yyyy-mm-dd HH:mm:ss'  
  
-   時刻: ' HH:mm:ss'  
  
 **日付形式の例**は次の表にします。  
  
 テーブルに関する注意:  
  
-   年、月、および日の形式と注文のさまざまなことができます。 テーブルには、ymd のみ表示されます。 月には、1 つまたは 2 桁の数字、または 3 つの文字を持つことができます。 1 日には、1 つまたは 2 桁の数字を持つことができます。 年には、2 ～ 4 桁の数字を持つことができます。  
  
-   ミリ秒 (fffffff) が必要ではありません。  
  
-   います pm (tt) は必要ありません。 既定では、AM は。  
  
|日付型|例|Description|  
|---------------|-------------|-----------------|  
|DateTime|DATE_FORMAT = 'yyyy-mm-dd HH:mm:ss.fff'|これに加えて、年、月、日、00 ～ 24 が含まれています時間、00 ～ 59 分を 00 ～ 59 秒、および 3 桁のミリ秒単位のです。|  
|DateTime|DATE_FORMAT = 'yyyy-mm-dd hh:mm:ss.ffftt'|これに加えて、年、月、日、00 ～ 12 が含まれています時間、00 ～ 59 分を 00 ～ 59 PM、または pm、秒、(ミリ秒単位) と、午前 3 桁の数字です。|  
|SmallDateTime|DATE_FORMAT = ' - yyyy-mm-dd HH:mm'|に加えて、年、月、および日の場合は、これが含まれます 00 ～ 23 には時間、00 ～ 59 分です。|  
|SmallDateTime|DATE_FORMAT = 'yyyy-mm-dd hh:mmtt'|これに加えて、年、月、および日の場合は、00-11 が含まれています時間、00 ～ 59 分、されません (秒単位) と AM、am、PM、または pm。|  
|日付|DATE_FORMAT = ' yyyy MM dd'|年、月、および日です。 Time 要素が含まれていない場合です。|  
|日付|DATE_FORMAT = ' yyyy-MMM-dd'|年、月、および日です。 月を指定するには 3 つの M のいずれか、または年 1 月、年 2 月、年 3 月、年 4 月、月、6 月 6 日、年 7 月、年 8 月、年 9 月、年 10 月、年 11 月、または年 12 月の文字列は入力の値です。|  
|DateTime2|DATE_FORMAT = 'yyyy-mm-dd HH:mm:ss.fffffff'|これに加えて、年、月、および日の場合は、00 ～ 23 が含まれています時間、00 ～ 59 分を 00 ～ 59 秒、およびミリ秒の 7 桁の数字です。|  
|datetime2|DATE_FORMAT = 'yyyy-mm-dd hh:mm:ss.ffffffftt'|これに加えて、年、月、および日の場合は、00-11 が含まれています時間、00 ～ 59 分を 00 ～ 59 PM、または pm、秒、(ミリ秒単位) と、午前 7 桁の数字です。|  
|DateTimeOffset|DATE_FORMAT = 'yyyy-mm-dd HH:mm:ss.fffffff zzz'|これに加えて、年、月、および日、00 ~ 23 が含まれています時間、00 ~ 59 分を 00 ~ 59 秒、および (ミリ秒単位) と、入力ファイルを配置するタイム ゾーン オフセットを 7 桁の数字 {+ (& a) #124;-} HH:ss です。 たとえば、Los Angeles 後 (夏時間) なしの節約は、UTC、-08 の値の背後にある、8 時間: 00 入力ファイルでは、ロサンゼルスのタイム ゾーンを指定します。|  
|DateTimeOffset|DATE_FORMAT = 'yyyy-mm-dd hh:mm:ss.ffffffftt zzz'|これに加えて、年、月、および日の場合は、00-11 が含まれています時間、00 ～ 59 分を 00 ～ 59 秒、ミリ秒、(AM、am、PM、または pm)、7 桁の数字、およびタイム ゾーン オフセット。 前の行の説明を参照してください。|  
|[時刻]|DATE_FORMAT = 'HH:mm:ss'|00 ～ 23 ののみ、日付の値はありません時間、00 ～ 59 分、および 00 ～ 59 秒。|  
  
 すべてには、日付の形式がサポートされています。  
  
|datetime|smalldatetime|date|datetime2|datetimeoffset|  
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
  
-   使用することができますか月、日、および年の値を分離するには、'-'、'/'、または ' です。 '. わかりやすくするために、テーブルは、'-' の区切りを使用します。  
  
-   指定するのには、テキストとして月は、次の 3 つ以上の文字を使用します。 か月間にわたり、1 ～ 2 文字は数値として解釈されます。  
  
-   時刻の値を分離するには、使用して、': ' 記号です。  
  
-   角かっこで囲まれた文字では、オプションです。  
  
-   文字 'tt' [AM| を指定します。PM|am|pm] です。 AM 既定値です。 'Tt' を指定すると、時間の値 (hh) は、0 ～ 12 の範囲でなければなりません。  
  
-   現在のタイム ゾーン形式で、システムのタイム ゾーン オフセットを指定する文字 'zzz' {+ |-} HH:ss] です。  
  
 USE_TYPE_DEFAULT = {TRUE |**FALSE** }  
 PolyBase がテキスト ファイルからデータを取得するときに、区切られたテキスト ファイル内の不足値を処理する方法を指定します。  
  
 TRUE  
 テキスト ファイルからデータを取得するときに、外部テーブルの定義に対応する列のデータ型の既定値を使用して、各の不足している値を格納します。 たとえばを使用して不足値に置き換えます。  
  
-   列が数値型の列として定義されている場合は、0 を返します。  
  
-   空の文字列""、列が文字列型の列である場合。  
  
-   1900-01-01 列が日付の列の場合。  
  
 FALSE  
 NULL としては、すべての不足値を格納します。 区切られたテキスト ファイルに null を使用して、格納されている任意の NULL 値は、文字列の 'NULL' としてインポートされます。  
  
   エンコード = {'UTF8' |UTF16'}   
 Azure SQL Data Warehouse に PolyBase は UTF8 と UTF16 LE エンコード区切りテキスト ファイルを読み取ることができます。 SQL Server PDW、PolyBase はサポートしていません UTF16 を読み取るファイルをエンコードします。
  
 DATA_COMPRESSION = *data_compression_method*  
 外部データに対するデータの圧縮方法を指定します。 DATA_COMPRESSION が指定されていない場合、既定値は、圧縮されていないデータはします。  
 適切に機能するために Gzip 圧縮ファイルにファイル拡張子が".gz"ことが必要です。
 
 DELIMITEDTEXT 書式の種類には、これらのメソッドの圧縮がサポートされています。  
  
-   データ圧縮 = 'org.apache.hadoop.io.compress.DefaultCodec'  
  
-   データ圧縮 = 'org.apache.hadoop.io.compress.GzipCodec'  

 RCFILE 書式の種類には、この圧縮メソッドがサポートされています。  
  
-   データ圧縮 = 'org.apache.hadoop.io.compress.DefaultCodec'  
  
 ORC ファイル形式の種類には、これらのメソッドの圧縮がサポートされています。  
  
-   データ圧縮 = 'org.apache.hadoop.io.compress.DefaultCodec'  
  
-   データ圧縮 = 'org.apache.hadoop.io.compress.SnappyCodec'  
  
 PARQUET ファイル形式の種類には、これらのメソッドの圧縮がサポートされています。  
  
-   データ圧縮 = 'org.apache.hadoop.io.compress.GzipCodec'  
  
-   データ圧縮 = 'org.apache.hadoop.io.compress.SnappyCodec'  
  
## <a name="permissions"></a>Permissions  
 任意の外部ファイル形式の ALTER 権限が必要です。  
  
## <a name="general-remarks"></a>全般的な解説  
 外部ファイル形式は、データベース スコープで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]です。 これは、サーバー スコープで[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。  
  
 形式オプションはすべてオプションと、区切られたテキスト ファイルにのみ適用されます。  
  
 圧縮された形式のいずれかで、データが保存されると、PolyBase は最初に展開されているデータ レコードを返す前にデータを使用します。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項   
  
 区切られたテキスト ファイルで、行区切り記号をサポートする必要がある Hadoop の LineRecordReader でつまりでなければ '\r'、'\n' または '\r\n' のいずれか。 ユーザー構成可能ではありません。  
  
 Rcfiles、サポートされている SerDe メソッドの組み合わせとサポートされているデータの圧縮方法は、この記事で以前表示されます。 すべての組み合わせがサポートされます。  
  
 PolyBase の同時実行クエリの最大数は、32 です。 32 の同時実行クエリが実行しているときに、各クエリは、外部のファイルの場所から 33,000 ファイルの最大を読み取ることができます。 ルート フォルダーと各サブフォルダーは、また、ファイルとしてカウントされます。 同時実行の程度が 32 未満である場合は、外部のファイルの場所は 33,000 複数のファイルを含めることができます。  
  
 制限のため、外部テーブル内のファイルの数を 30,000 より小さいファイルを保存するルートと、外部のファイルの場所のサブフォルダーをお勧めします。 また、ルート ディレクトリの下のサブフォルダーの数を小さい数にすることをお勧めします。 ファイルが多すぎますが参照されている場合、Java 仮想マシンのメモリ不足の例外が発生する可能性があります。  
  
## <a name="locking"></a>ロック  
 外部のファイル形式のオブジェクトには、共有ロックを取得します。  
  
## <a name="performance"></a>パフォーマンス  
 常に圧縮されたファイルを使用してには、バランスを取るようにして、データの圧縮 CPU 使用率の向上と、外部データ ソースと SQL Server の間でのデータを転送する間あります。  
  
 Gzip 圧縮されたテキスト ファイルが分割可能ではありません。 Gzip 圧縮されたテキスト ファイルのパフォーマンスを向上させるには、外部データ ソース内の同じディレクトリに格納されている複数のファイルを生成するをお勧めします。 これにより、PolyBase を読み取って、複数のリーダーと圧縮解除のプロセスを使用して、高速のデータを圧縮解除できます。 圧縮されたファイルの適切な数は、コンピューティング ノードごとのデータ リーダーのプロセスの最大数です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、データ リーダーのプロセスの最大数は、現在のリリースでノードあたり 8 です。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]、ノードごとのデータ リーダーのプロセスの最大数は、SLO によって異なります。 参照してください[Azure SQL データ ウェアハウスのパターンと戦略を読み込み](https://blogs.msdn.microsoft.com/sqlcat/2016/02/06/azure-sql-data-warehouse-loading-patterns-and-strategies/)詳細についてはします。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-create-a-delimitedtext-external-file-format"></a>A. DELIMITEDTEXT 外部ファイル形式を作成します  
 この例は、外部ファイル形式の名前付き*textdelimited1*テキスト区切りのファイルです。 ファイル内のフィールドが、パイプ文字で区切られるように、FORMAT_OPTIONS の指定 ' |'。 テキスト ファイルは Gzip コーデックで圧縮されます。 DATA_COMPRESSION が指定されていない場合は、テキスト ファイルが圧縮されていません。  
  
 区切られたテキスト ファイルの場合は、データの圧縮方法できます、既定のコーデック、'org.apache.hadoop.io.compress.defaultcodec'、または Gzip コーデック 'org.apache.hadoop.io.compress.gzipcodec' です。  
  
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
  
### <a name="b-create-an-rcfile-external-file-format"></a>B. RCFile の外部ファイル形式を作成します。  
 この例では、シリアル化または逆シリアル化メソッドの org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe を使用する RCFile の外部のファイル形式を作成します。 データの圧縮方法の既定のコーデックを使用することも指定します。 DATA_COMPRESSION が指定されていない場合、既定の圧縮はありません。  
  
```  
CREATE EXTERNAL FILE FORMAT rcfile1  
WITH (  
    FORMAT_TYPE = RCFILE,  
    SERDE_METHOD = 'org.apache.hadoop.hive.serde2.columnar.LazyBinaryColumnarSerDe',  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.DefaultCodec'  
);  
```  
  
### <a name="c-create-an-orc-external-file-format"></a>C. ORC の外部のファイル形式を作成します。  
 この例では、org.apache.io.compress.SnappyCodec データ圧縮方法でデータを圧縮する ORC ファイルの外部のファイル形式を作成します。 DATA_COMPRESSION が指定されていない場合、既定の圧縮はありません。  
  
```  
CREATE EXTERNAL FILE FORMAT orcfile1  
WITH (  
    FORMAT_TYPE = ORC,  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.SnappyCodec'  
);  
```  
  
### <a name="d-create-a-parquet-external-file-format"></a>D. PARQUET 外部ファイル形式を作成します  
 この例では、org.apache.io.compress.SnappyCodec データ圧縮方法でデータを圧縮する Parquet ファイルの外部のファイル形式を作成します。 DATA_COMPRESSION が指定されていない場合、既定の圧縮はありません。  
  
```  
CREATE EXTERNAL FILE FORMAT parquetfile1  
WITH (  
    FORMAT_TYPE = PARQUET,  
    DATA_COMPRESSION = 'org.apache.hadoop.io.compress.SnappyCodec'  
);  
```  
  
## <a name="see-also"></a>参照  
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)   
 [EXTERNAL TABLE AS SELECT &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-external-table-as-select-transact-sql.md)   
 [テーブルとして選択 &#40; を作成します。Azure SQL Data Warehouse &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)   
 [sys.external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)  
  
  

