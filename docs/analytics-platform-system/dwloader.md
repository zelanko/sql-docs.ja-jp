---
title: dwloader のコマンドラインのローダーの Parallel Data Warehouse |Microsoft Docs
description: dwloader は、既存のテーブルに一括でテーブルの行をロードする並列データ ウェアハウス (PDW) コマンド ライン ツールです。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: df30a9b849b987b5514a1824f25736a82587da09
ms.sourcegitcommit: 982a1dad0b58315cff7b54445f998499ef80e68d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66175036"
---
# <a name="dwloader-command-line-loader-for-parallel-data-warehouse"></a>dwloader の Parallel Data Warehouse 用のコマンド ライン ローダー
**dwloader の**は既存のテーブルに一括でテーブルの行をロードする並列データ ウェアハウス (PDW) コマンド ライン ツールです。 行を読み込むときに、テーブルの末尾にすべての行を追加することができます (*追加モード*または*fastappend モード*)、新しい行が追加および既存の行を更新 (*upsert モード*)、またはすべてを削除します。既存の行を読み込む前に、空のテーブルにすべての行を挿入 (*モードを再読み込み*)。  
  
**データを読み込むためのプロセス**  
  
1.  ソース データを準備します。  
  
    読み込むソース データを作成するのにには、独自の ETL プロセスを使用します。 ソース データは、レプリケーション先テーブルのスキーマに合わせて書式設定する必要があります。 1 つまたは複数のテキスト ファイルにソース データを格納し、テキスト ファイルを読み込み、サーバー上の同じディレクトリにコピーします。 読み込みサーバーについては、次を参照してください[の取得と読み込みのサーバーの構成。](acquire-and-configure-loading-server.md)  
  
2.  読み込みオプションを準備します。  
  
    使用する読み込みオプションを決定します。 構成ファイルの読み込みオプションを格納します。 構成ファイルを読み込み、サーバー上のローカルの場所にコピーします。 **Dwloader**構成オプションは、このトピックで説明されています。  
  
3.  エラー時のオプションの負荷を準備します。  
  
    方法を決める**dwloader**読み込みに失敗した行を処理します。 読み込みが実行する**dwloader**ステージング テーブルにデータを初めて読み込まれ、先のテーブルにデータを転送します。 ローダーでは、ステージング テーブルにデータが読み込まれる、読み込みに失敗した行の数を追跡します。 たとえば、正しくフォーマットされていない行は読み込みに失敗します。 失敗した行は、拒否ファイルにコピーされます。 既定では、負荷を別の却下のしきい値を指定しない限り、最初の拒否の後に中止します。  
  
4.  インストール**dwloader**します。  
  
    インストールされていない場合は、dwloader 読み込みサーバーをインストールします。 

<!-- MISSING LINK
    See [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](install-dwloader-command-line-loader-sql-server-pdw.md). 
--> 
  
5.  実行**dwloader**します。  
  
    読み込みサーバーにサインインし、実行可能ファイル実行**dwloader.exe**適切なコマンド ライン オプションを使用します。  
  
6.  結果を確認します。  
  
    失敗をチェックする行 (-R で指定された) ファイルを読み込む任意の行が失敗したかどうかを参照してください。 このファイルが空の場合は、すべての行が正常に読み込まれます。 **dwloader の**は場合、いずれかの手順 (拒否された行以外) が失敗では、すべての手順にロールバックを初期状態にあるために、トランザクション、します。  
  
<!-- 
![Topic link icon](media/topic-link.gif "Topic_Link")[Syntax Conventions](syntax-conventions-sql-server-pdw.md)  
-->  


## <a name="syntax"></a>構文  
  
```  
dwloader.exe { -h }  
  
dwloader.exe   
    {  
        { -U login_name  -P password  }  
        | -W  
    }  
    [ -f parameter_file ]  
    [ -S target_appliance ]  
    { -T target_database_name . [ schema ] . table_name }   
    { -i source_data_location } [ <source_data_options> ]  
    { -R load_failure_file_name } [ <load_failure_options> ]  
    [ <loading_options> ]  
}  
  
<source_data_options> ::=  
{  
    [ -fh number_header_rows ]  
    [ < variable_length_column_options > | < fixed_width_column_options > ]  
    [ -D { mdy | myd | ymd | ydm | dmy | dym | custom_date_format } ]  
    [ -dt datetime_format_file ]  
}  
  
<variable_length_column_options> ::=  
{  
    [ -e character_encoding ]  
    -r row_delimiter   
    [ -s string_delimiter ]  
    -t field_delimiter   
}  
  
<fixed_width_column_options> ::=  
{  
    -w fixed_width_config_file   
    [ -e character_encoding ]   
    -r row_delimiter   
}  
  
<load_failure_options> ::=  
{  
    [ -rt { value | percentage } ]  
    [ -rv reject_value ]  
    [ -rs reject_sample_value ]  
}  
  
<loading_options> ::=  
{  
    [ -d staging_database_name ]  
    [ -M { append | fastappend | upsert -K merge_column [ ,...n ] | reload } ]  
    [ -b batchsize ]   
    [ -c ]  
    [ -E ]  
    [ -m ]  
    [ -N ]  
    [ -se ]
    [ -l ]   
}  
```  
  
## <a name="arguments"></a>引数  
**-h**  
ローダーの使用方法に関する簡単なヘルプ情報が表示されます。 ヘルプは、その他のコマンド ライン パラメーターが指定されていない場合にのみ表示されます。  
  
**-U** *login_name*  
負荷を実行する適切なアクセス許可を持つ有効な SQL Server 認証ログイン。  
  
**-P** *password*  
SQL Server の認証のパスワード*login_name*します。  
  
**-W**  
Windows 認証を使用します。 (いいえ*login_name*または*パスワード*必要です)。 

<!-- MISSING LINK
For information about configuring Windows Authentication, see [Security - Configure Domain Trusts](security-configure-domain-trusts.md).  
-->
  
**-f** *parameter_file_name*  
パラメーター ファイルを使用して*parameter_file_name*、コマンド ライン パラメーターの代わりにします。 *parameter_file_name*以外のコマンド ライン パラメーターを含めることができます*user_name*と*パスワード*します。 パラメーターを指定するコマンドラインとパラメーター ファイルで、コマンド ラインは、file パラメーターをオーバーライドします。  
  
なし、パラメーター ファイルに 1 つのパラメーターが含まれています、 **-** 1 行のプレフィックス。  
  
例 :  
  
`rt=percentage`  
  
`rv=25`  
  
* *-S***target_appliance*  
読み込まれたデータを受信する SQL Server PDW アプライアンスを指定します。  
  
*Infiniband 接続*、 *target_appliance* < アプライアンス名 > として指定されて-SQLCTL01 します。 この接続を名前付きを構成するを参照してください。 [InfiniBand ネットワーク アダプターの構成](configure-infiniband-network-adapters.md)します。  
  
イーサネット接続の場合は、 *target_appliance*はコントロールのノード クラスターの IP アドレスです。  
  
省略した場合、dwloader dwloader のインストール時に指定された値に既定値です。 

<!-- MISSING LINK
For more information about this install option, see [Install dwloader Command-Line Loader](install-dwloader.md).  
-->
  
**-T** *target_database_name.* [*schema*].*table_name*  
変換先テーブルの 3 つの部分の名前。  
  
* *-I***source_data_location*  
読み込みに 1 つまたは複数のソース ファイルの場所。 各ソース ファイルは、テキスト ファイルまたは gzip で圧縮されているテキスト ファイルである必要があります。 Gzip ファイルごとに 1 つだけのソース ファイルを圧縮できます。  
  
ソース ファイルの書式を設定します。  
  
-   ソース ファイルは、読み込みのオプションに従って書式設定する必要があります。  
  
-   ソース ファイル内の各行には、1 つのテーブル行のデータが含まれています。 ソース データは、変換先テーブルのスキーマに一致する必要があります。 列の順序およびデータ型も一致する必要があります。 行の各フィールドは、変換先テーブル内の列を表します。  
  
-   既定では、フィールドは、可変長と区切り記号で区切られました。 区切り記号の種類を指定するには、< variable_length_column_options > コマンド ライン オプションを使用します。 固定長のフィールドを指定するには、< fixed_width_column_options > コマンド ライン オプションを使用します。  
  
ソース データの場所を指定します。  
  
-   ソース データの場所には、ネットワーク パスまたは読み込みサーバー上のディレクトリへのローカル パスを指定できます。  
  
-   ディレクトリ内のすべてのファイルを指定するには、後に、ディレクトリ パスを入力、* ワイルドカード文字です。  ローダーでは、ソース データの場所にある任意のサブディレクトリからのファイルを読み込みません。 Gzip ファイルにディレクトリが存在する場合のローダーのエラーです。  
  
-   ディレクトリ内には、一部のファイルを指定するには、文字の組み合わせを使用して、* ワイルドカードです。  
  
1 つのコマンドを使用して複数のファイルを読み込めません。  
  
-   すべてのファイルは、同じディレクトリに存在する必要があります。  
  
-   ファイルは、すべてのテキスト ファイル、すべての gzip ファイルまたはテキストと gzip ファイルの両方の組み合わせである必要があります。  
  
-   ファイルは、ヘッダー情報を含めることができます。  
  
-   すべてのファイルには、同じ文字のエンコードの種類を使用する必要があります。 -E オプションを参照してください。  
  
-   すべてのファイルは、同じテーブルに読み込む必要があります。  
  
-   すべてのファイルは連結し、1 つのファイルは、拒否された行が却下の 1 つのファイルに移動する のように読み込まれます。  
  
例 :  
  
-   -i \\\loadserver\loads\daily\\*.gz  
  
-   -i \\\loadserver\loads\daily\\*.txt  
  
-   -i \\\loadserver\loads\daily\monday.*  
  
-   -i \\\loadserver\loads\daily\monday.txt  
  
-   -i \\\loadserver\loads\daily\\*  
  
**-R** *load_failure_file_name*  
読み込みのエラーがある場合**dwloader**という名前のファイルのエラー情報は、ロード テストと失敗の説明に失敗した行を格納*load_failure_file_name*します。 このファイルが既に存在する場合、dwloader は既存のファイルを上書きします。 *load_failure_file_name*最初のエラーが発生したときに作成されます。 すべての行が正常に読み込む場合*load_failure_file_name*は作成されません。  
  
**-fh** *number_header_rows*  
先頭を無視する行 (行) の数*source_data_file_name*します。 既定値は 0 です。  
  
<variable_length_column_options>  
オプション、 *source_data_file_name*文字で区切られた可変長列を持ちます。 既定では、 *source_data_file_name* ASCII 文字可変長列にはが含まれています。  
  
ASCII ファイルの場合は、null 値は区切り記号を連続して配置することで表されます。 たとえば、パイプで区切られたファイルで ("|") で null 値が示される"| |"です。 示される null 値のコンマ区切りのファイルでは、「、」。 さらに、 **-e** (--emptyStringAsNull) オプションを指定する必要があります。 -E の詳細については、以下を参照してください。  
  
**-e** *character_encoding*  
データ ファイルから読み込まれるデータの文字エンコーディング型を指定します。 (既定値) の ASCII、UTF8、UTF16、または UTF16BE、UTF16 リトル エンディアンあり UTF16BE はビッグ エンディアンこともできます。 これらのオプションは、大文字小文字を区別します。  
  
**-t** *field_delimiter*  
各フィールド (列)、行区切り記号。 フィールド区切り記号は、これらのエスケープ文字の ASCII または ASCII の 16 進値の 1 つ以上です。  
  
|名前|エスケープ文字|16 進の文字|  
|--------|--------------------|-----------------|  
|タブ|\t|0x09|  
|キャリッジ リターン (CR)|\r|0x0d|  
|ライン フィード (LF)|\n|0x0a|  
|CRLF|\r\n|0x0d0x0a|  
|コンマ|','|0x2c|  
|二重引用符|\\"|0x22|  
|単一引用符|\\'|0x27|  
  
コマンドラインでは、パイプ文字を指定するには二重引用符で囲みます"|"です。 これにより、コマンド ライン パーサーによって誤ってトライグラフとして解釈が回避されます。 その他の文字は単一引用符で囲まれます。  
  
例 :  
  
-t "|"  
  
-t ' '  
  
-t 0x0a  
  
-t \t  
  
-t '~|~'  
  
**-r** *row_delimiter*  
ソース データ ファイルの各行の区切り記号。 行区切り記号は、1 つまたは複数の ASCII 値です。  
  
キャリッジ リターン (CR)、改行 (LF)、またはタブ文字を区切り記号として指定するには、エスケープ文字 (\r、\n、\t) やその 16 進数の値 (0 x、09、0 d) を使用できます。 区切り文字として他の特殊文字を指定するには、16 進数の値を使用します。  
  
CR LF + の例:  
  
-r \r\n  
  
-r 0x0d0x0a  
  
CR の例:  
  
-r \r  
  
-r 0x0d  
  
LF の例:  
  
-r \n  
  
-r 0x0a  
  
LF では、Unix の必要があります。 CR は、Windows に必要です。  
  
**-s** *string_delimiter*  
文字列データの区切り記号は、テキスト区切りの入力ファイルのフィールドを入力します。 文字列の区切り記号は、1 つまたは複数の ASCII 値です。  文字として指定できます (例: s *) または 16 進値 (例:-s 0x22 の二重引用符)。  
  
例 :  
  
-s *  
  
-s 0x22  
  
< fixed_width_column_options>  
固定長列を持つソース データ ファイルのオプション。 既定では、 *source_data_file_name* ASCII 文字可変長列にはが含まれています。  
  
-E は UTF8 ときに、固定幅列はサポートされていません。  
  
**-w** *fixed_width_config_file*  
パスと各列の文字数を指定する構成ファイルの名前。 すべてのフィールドを指定する必要があります。  
  
このファイルは、読み込みサーバー上に存在する必要があります。 パスは、UNC、相対パス、または絶対パスを指定できます。 内の各行*fixed_width_config_file*その列の 1 つの列と文字数の名前が含まれています。 次のように、列、ごとに 1 行があるし、ファイル内の順序が変換先テーブル内の順序と一致する必要があります。  
  
*column_name*=*num_chars*  
  
*column_name*=*num_chars*  
  
固定幅の構成ファイルの例:  
  
SalesCode=3  
  
SalesID = 10  
  
線の例*source_data_file_name*:  
  
230Shirts0056  
  
320Towels1356  
  
前の例では、最初に読み込まれた行が SalesCode = '230' と SalesID = 'Shirts0056'。 読み込まれた 2 つ目の行になります SalesCode = '320' と SaleID = 'Towels1356'。  
  
先頭および末尾の固定幅モードで、スペースやデータの型変換を処理する方法については、次を参照してください。[データ型の変換規則 dwloader の](dwloader-data-type-conversion-rules.md)します。  
  
**-e** *character_encoding*  
データ ファイルから読み込まれるデータの文字エンコーディング型を指定します。 (既定値) の ASCII、UTF8、UTF16、または UTF16BE、UTF16 リトル エンディアンあり UTF16BE はビッグ エンディアンこともできます。 これらのオプションは、大文字小文字を区別します。  
  
-E は UTF8 ときに、固定幅列はサポートされていません。  
  
**-r** *row_delimiter*  
ソース データ ファイルの各行の区切り記号。 行区切り記号は、1 つまたは複数の ASCII 値です。  
  
キャリッジ リターン (CR)、改行 (LF)、またはタブ文字を区切り記号として指定するには、エスケープ文字 (\r、\n、\t) やその 16 進数の値 (0 x、09、0 d) を使用できます。 区切り文字として他の特殊文字を指定するには、16 進数の値を使用します。  
  
CR LF + の例:  
  
-r \r\n  
  
-r 0x0d0x0a  
  
CR の例:  
  
-r \r  
  
-r 0x0d  
  
LF の例:  
  
-r \n  
  
-r 0x0a  
  
LF では、Unix の必要があります。 CR は、Windows に必要です。  
  
**-D** { **ymd** | ydm | mdy | myd |  dmy | dym | *custom_date_format* }  
入力ファイルでは、月 (m)、1 日 (d)、および datetime フィールドのすべての年 (y) の順序を指定します。 既定の順序は、ymd です。 同じソース ファイルの複数の注文形式を指定するには、-dt オプションを使用します。  
  
ymd | dmy  
ydm と dmy は、同じ入力形式を使用できます。 どちらも、年の日付の前後であります。 両方の例では、 **ydm**と**dmy**日付の書式、入力ファイルの 2013-02-03 または 02-03-2013 がある可能性があります。  
  
ydm  
Ydm 形式のデータ型 datetime および smalldatetime の列に入力のみを読み込むことができます。 Ydm 値は、datetime2、日付、または datetimeoffset データ型の列に読み込むことはできません。  
  
mdy  
年 (mdy) により<month> <space> <day> <comma><year>します。  
  
1975 年 1 月 1 日の年 (mdy) 入力データの例:  
  
-   1975 年 1 月 1 日  
  
-   Jan 01日 75  
  
-   年 1 月/1/75  
  
-   01011975  
  
myd  
3 月のファイルの例を入力 04,2010。03-2010-04, 3/2010/4  
  
dym  
入力ファイルでは、2010 年 3 月 4 日の例:04-2010-03, 4/2010/3  
  
*custom_date_format*  
*custom_date_format*カスタム日付形式は、(例: 年/月/日) 旧バージョンとの互換性を保つのために含まれるとします。 dwloader のでは、カスタムの日付の書式は適用されません。 代わりに、カスタム日付形式を指定する**dwloader** ymd、ydm、年 (mdy)、myd、dym、または dmy の対応する設定に変換されます。  
  
たとえば、-d 年/月/日を指定すると dwloader のすべての日付の最初に、1 か月の注文を入力し、日、年 (mdy) し、期待しています。 2 文字の数か月、2 桁の日、およびカスタム日付形式で指定された 4 桁の年は適用されません。 日付形式は、-d 年/月/日の場合、入力ファイルで日付を形式指定できる方法の例をいくつか次に示します。01/02/2013、Jan.02.2013、2013 年 1 月 2  
  
包括的な書式設定については、次を参照してください。[データ型の変換規則 dwloader の](dwloader-data-type-conversion-rules.md)します。  
  
**-dt** *datetime_format_file*  
各 datetime 形式がという名前のファイルで指定された*datetime_format_file*します。 コマンドラインのパラメーターとは異なりスペースが含まれるファイルのパラメーターを二重引用符で囲んでいない必要があります。 データを読み込むよう、datetime 形式を変更することはできません。 ソース データ ファイルと、対応する列を変換先テーブルでは、同じ形式が必要です。  
  
各行には、変換先テーブルとその datetime 形式での列の名前が含まれています。  
  
例 :  
  
`LastReceiptDate=ymd`  
  
`ModifiedDate=dym`  
  
**-d** *staging_database_name*  
ステージング テーブルを格納するデータベース名。 既定では、変換先テーブルのデータベースは-t オプションで指定されたデータベースです。 詳細については、ステージング データベースを使用して、次を参照してください。[ステージング データベース作成](staging-database.md)です。  
  
**-M** *load_mode_option*  
追加、アップサート、またはデータを再読み込みするかどうかを指定します。 既定のモードを追加します。  
  
append  
ローダーは、変換先テーブル内の既存の行の末尾に行を挿入します。  
  
fastappend  
ローダーは、変換先テーブルの既存の行の末尾に、一時テーブルを使用せず、直接、行を挿入します。 fastappend には、複数のトランザクションが必要です。 (-m) オプション。 Fastappend を使用する場合、ステージング データベースを指定することはできません。 読み込みプロセスが中止されたかどうかの負荷からの復旧を処理する必要がおり、fastappend とロールバックは行われません。  
  
upsert **-K**  *merge_column* [ ,...*n* ]  
ローダーでは、SQL Server マージ ステートメントを使用して、既存の行を更新し、新しい行を挿入します。  
  
-K オプションでは、マージの基になる列を指定します。 これらの列は、主キー、一意の行を表す必要がありますを形成します。 変換先テーブルに主キーが存在する場合、行が更新されます。 変換先テーブルに主キーが存在しない場合は、行が追加されます。  
  
ハッシュ分散テーブルは、主キーがするか、ディストリビューション列を含める必要があります。  
  
レプリケートされたテーブルの場合は、主キーは、1 つまたは複数の列の組み合わせです。 アプリケーションのニーズに合わせて、これらの列が指定されます。  
  
スペースなしで、コンマまたはスペースを含むコンマ区切りと単一引用符で囲まれた複数の列があります。  
  
ソース テーブル内の 2 つの行のマージ キーの値が一致する場合は、それぞれの行と同じである必要があります。  
  
再読み込み  
ソース データを挿入する前に、ローダーは、変換先テーブルを切り捨てます。  
  
**-b** *batchsize*  
Microsoft サポートによる使用はのみ推奨*batchsize* DMS が、コンピューティング ノード上の SQL Server インスタンスを実行する一括コピーのバッチ サイズを SQL Server。  ときに*batchsize*を指定すると、SQL Server PDW は各負荷を動的に計算されるバッチ読み込みサイズをオーバーライドします。  
  
以降では、SQL Server 2012 PDW は、制御ノードは、既定で各読み込みのバッチ サイズを動的に計算します。 この自動計算は、メモリ サイズ、ターゲット テーブルの種類、対象テーブルのスキーマ、負荷の種類、ファイルのサイズ、およびユーザーのリソース クラスなどのいくつかのパラメーターに基づきます。  
  
たとえば、ロード モードに FASTAPPEND があり、ユーザーがテーブルにクラスター化列ストア インデックスは、SQL Server PDW は既定値は 1,048, 576 のバッチ サイズを使用して、行グループが終了になるようにしようして負荷を直接列ストアを経由せず、デルタ ストア。 メモリが 1,048, 576 のバッチ サイズを許可していない場合、dwloader は小さい batchsize を選択します。  
  
FASTAPPEND、負荷の種類の場合、 *batchsize*それ以外の場合、テーブルにデータの読み込みに適用されます*batchsize*ステージング テーブルにデータの読み込みに適用されます。  
  
<reject_options>  
ローダーにより、読み込みエラーの数を決定するためのオプションを指定します。 読み込みエラーがしきい値を超えた場合、ローダーは停止し、任意の行をコミットできません。  
  
**-rt** { **value** | percentage }  
指定するかどうかは、*reject_value*で、 **-rv** *reject_value*オプションは、行 (値) のリテラルの数または失敗 (割合) の割合。 既定では、値は。  
  
割合のオプションは、-rs オプションに基づいて間隔で発生するリアルタイム計算です。  
  
たとえば、100 行と 25 を読み込むローダーの試行が失敗し、75 が成功する場合、25% が失敗率にします。  
  
**-rv** *reject_value*  
負荷を停止する前に許可する数または行の却下のパーセンテージを指定します。 **-Rt**場合オプションを決定します*reject_value*行数または行の割合を表します。  
  
既定の*reject_value*は 0 です。  
  
-Rt 値と共に使用すると、ローダーは、拒否された行の数が reject_value を超えると、負荷を停止します。  
  
-Rt 割合で使用する場合、ローダーは、間隔で、比率を計算 (-rs オプション)。 そのため、失敗した行の割合を超える*reject_value*します。  
  
**-rs** *reject_sample_size*  
使用される、`-rt percentage`増分割合チェックを指定するオプション。 たとえば、reject_sample_size が 1000 の場合は、ローダー比率が計算されます、失敗した行の 1000 行の読み込みを試みた後にします。 各追加の 1000 行の読み込みを試行した後、失敗した行の割合が再計算します。  
  
**-c**  
左から char、nchar、varchar、nvarchar のフィールドの右側にある空白文字を削除します。 空の文字列に空白文字だけを含む各フィールドに変換します。  
  
例 :  
  
'        ' gets truncated to ''  
  
'abc' は 'abc' に切り捨てられます  
  
C に-e を使用すると、-e の操作に最初に発生します。 空白文字だけが含まれているフィールドは、空の文字列と NULL に変換されます。  
  
**-E**  
空の文字列を NULL に変換します。 既定値では、これらの変換を実行しないようにします。  
  
**-m**  
読み込みの 2 番目のフェーズに複数のトランザクション モードを使用します。ときに、分散テーブルにステージング テーブルからデータを読み込んでいます。  
  
**-M**、SQL Server PDW を実行し、並列読み込みをコミットします。 これは、既定のモードでの読み込みよりもかなり速くが、トランザクションの安全なではありません。  
  
せず **-m**、SQL Server PDW を実行し、各コンピューティング ノード内で、ディストリビューション間で同時にコンピューティング ノード間で負荷を逐次的にコミットします。 このメソッドは、複数のトランザクション モードより低速ですが、トランザクションの安全なは。  
  
**-m**は省略可能です*追加*、*を再読み込み*、および*upsert*します。  
  
**-m** fastappend が必要です。  
  
**-m**レプリケートされたテーブルでは使用できません。  
  
**-m**読み込みの 2 番目のフェーズにのみ適用されます。 最初の読み込みフェーズ; には適用されません。ステージング テーブルにデータを読み込んでいます。  
  
読み込みプロセスによって中止されたかどうかの負荷からの復旧を処理する必要がありますが、複数のトランザクション モードでのロールバックは行われません。  
  
使用することをお勧めします。 **-m**データを失わずに回復できるように、空のテーブルに読み込む場合にのみです。 読み込みエラーから回復する: を変換先テーブルを削除して負荷の問題を解決する、変換先テーブルを再作成し、読み込みをもう一度実行します。  
  
**-N**  
ターゲット アプライアンスが信頼された証明機関から有効な SQL Server PDW の証明書を確認します。 これを使用して、対象外のデータを確保しやすくが攻撃者によって盗ま、不正な場所に送信します。 証明書は、アプライアンスに既にインストールする必要があります。 証明書をインストールする唯一の方法では、アプライアンス管理者は、Configuration Manager ツールを使用してインストールします。 かどうかかわからないアプライアンスがインストールされている信頼された証明書を持つかどうかは、アプライアンス管理者に問い合わせてください。  
  
**-se**  
空のファイルの読み込みをスキップします。 これも空の gzip ファイルを圧縮解除をスキップします。

**-l**  
CU7.4 更新により、利用可能では、読み込むことができるバイト単位での行の最大長を指定します。 有効な値は、32768 と 33554432 間の整数です。 のみ、必要なときに使用して、これは、クライアントとサーバーでより多くのメモリを割り当てます (32 KB より大きい) サイズの大きい行を読み込みます。
  
## <a name="return-code-values"></a>リターン コードの値  
0 (成功) またはその他の整数値 (失敗)  
  
コマンド ウィンドウまたはバッチ ファイルを使って`errorlevel`リターン コードを表示します。 以下に例を示します。  
  
```  
dwloader  
echo ReturnCode=%errorlevel%  
if not %errorlevel%==0 echo Fail  
if %errorlevel%==0 echo Success  
```  
  
PowerShell を使用する場合を使用して、`$LastExitCode`します。  
  
## <a name="permissions"></a>アクセス許可  
負荷および変換先テーブルに適用可能なアクセス許可 (INSERT、UPDATE、DELETE) が必要です。 ステージング データベース (一時テーブルの作成) に対する作成アクセス許可が必要です。 ステージング データベースを使用しない場合は、転送先データベースに作成するアクセス許可が必要です。 

<!-- MISSING LINK
For more information, see [Grant permissions to load data](grant-permissions-to-load-data.md).  
-->
  
## <a name="general-remarks"></a>全般的な解説  
Dwloader の読み込み時に、データ型変換については、次を参照してください。[データ型の変換規則 dwloader の](dwloader-data-type-conversion-rules.md)します。  
  
パラメーターには、1 つ以上のスペースが含まれている場合は、二重引用符でパラメーターを囲みます。  
  
インストール場所から、ローダーを実行する必要があります。 Dwloader の実行可能ファイルは、アプライアンスが事前インストールされているし、は C:\Program files \microsoft SQL Server データ Warehouse\DWLoader ディレクトリにあります。  
  
パラメーター ファイルで指定されているパラメーターをオーバーライドすることができます (-f オプション) コマンド ライン パラメーターとして指定します。  
  
ローダーの複数のインスタンスを同時に実行することができます。 ローダーのインスタンスの最大数は、事前構成され、は変更できません。 

<!-- MISSING LINK
For the maximum number of loads per appliance, see [Minimum and Maximum Values](minimum-maximum-values.md)  
-->
  
読み込まれたデータは、ソースの場所により、アプライアンス上の領域より小さいか必要があります。 ディスクの消費量を推定するデータのサブセットでテストのインポートを行うことができます。  
  
**Dwloader**トランザクション プロセスしはロールバック適切に失敗した場合、一括読み込みが正常に完了した後に戻すロールバックすることはできません。 アクティブなをキャンセルする**dwloader**プロセスは、CTRL キーを押しながら C キーを入力します。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
同時に発生した、データベースの LOG_SIZE よりも小さくして、すべての同時読み込みの合計サイズをお勧めする必要がありますすべての負荷の合計サイズは、LOG_SIZE の 50% 未満です。 このサイズの制限を実現するためには、複数のバッチに大きな負荷を分割できます。 LOG_SIZE の詳細については、次を参照してください[データベースの作成。](../t-sql/statements/create-database-parallel-data-warehouse.md)  
  
1 つの負荷のコマンドを使用して複数のファイルを読み込むときに、拒否されたすべての行が同じ拒否ファイルに書き込まれます。 拒否ファイルは、拒否された行を含む入力ファイルは表示されません。  
  
区切り記号として空の文字列を使用しない必要があります。 行区切り記号として空の文字列を使用すると、負荷が失敗します。 負荷が、区切り記号を無視し、既定値を使用する続行列区切り記号として使用するときに"|"列の区切り記号として。 文字列の区切り記号として使用する場合、空の文字列は無視され、既定の動作が適用されます。  
  
## <a name="locking-behavior"></a>ロック動作  
**dwloader の**ロック動作によって異なります、 *load_mode_option*します。  
  
-   **追加**-追加は、推奨されるあり、最も一般的なオプションです。 ステージング テーブルにデータを読み込みますを追加します。 ロックは、以下で詳しく説明します。  
  
-   **高速追加**-高速追加 ExclusiveUpdate テーブル ロックでは、最終的なテーブルに直接読み込み、ステージング テーブルを使用しない唯一のモードです。  
  
-   **再読み込み**-の再読み込みがステージング テーブルにデータをロードおよびステージング テーブルと最終的なテーブルの両方に対する排他ロックが必要です。 同時実行操作は、再読み込みはお勧めしません。  
  
-   **upsert** -アップサート ステージング テーブルにデータをロードおよび最終的なテーブルにステージング テーブルからマージ操作を実行します。 Upsert では、最終的なテーブルに排他ロックは必要ありません。 Upsert を使用する場合、パフォーマンスが異なる場合があります。 環境内で動作をテストします。  
  
### <a name="locking-behavior"></a>ロック動作  
**ロックのモードを追加します。**  
  
追加 (-m 引数を使用して) 複数のトランザクション モードで実行できますが、トランザクションの安全ではありません。 そのための追加 (-m 引数を使用) せずにトランザクション操作として使用する必要があります。 残念ながら、最終的な INSERT SELECT 操作中にトランザクション モードが現在約 6 倍よりも低い複数のトランザクション モードです。  
  
Append モードでは、2 つのフェーズでデータを読み込みます。 第 1 フェーズでは、ステージング テーブルを同時に (断片化が発生することができます) に、ソース ファイルからデータを読み込みます。 フェーズ 2 では、最終的なテーブルにステージング テーブルからデータを読み込みます。 2 番目のフェーズを実行する**INSERT INTO.選択 WITH (TABLOCK)** 操作。 追加モードのログ記録の動作を使用する場合と、次の表は、最終的なテーブルで、ロックの動作を示しています。  
  
|テーブル型|複数のトランザクション<br />モード (-m)|テーブルが空です。|同時実行のサポート|ログの記録|  
|--------------|-----------------------------------|------------------|-------------------------|-----------|  
|ヒープ|はい|[はい]|はい|最小限|  
|ヒープ|はい|いいえ|はい|最小限|  
|ヒープ|いいえ|はい|いいえ|最小限|  
|ヒープ|いいえ|いいえ|いいえ|最小限|  
|cl|はい|[はい]|いいえ|最小限|  
|cl|はい|いいえ|はい|[完全]|  
|cl|いいえ|はい|いいえ|最小限|  
|cl|いいえ|いいえ|はい|[完全]|  
  
上記の表に示す**dwloader**ヒープまたはクラスター化インデックス (CI) テーブル、トランザクションで複数のフラグの有無に読み込むと、空のテーブルまたは空でないテーブルに読み込む追加モードを使用します。 ロックとログ記録の負荷のようなそれぞれの組み合わせの動作は、テーブルに表示されます。 たとえばの append モードで (2) フェーズの読み込みとテーブル PDW テーブルに排他ロックを作成するにはマルチ トランザクション モードを使用せず、クラスター化インデックスと、空にログ記録は最小限です。 つまり、顧客は空のテーブルに (2) フェーズとクエリを同時にロードできません。 ただし、PDW は、テーブルに対する排他ロックを発行しませんと空でないテーブルに同じ構成を読み込むときに、同時実行が可能。 残念ながら、完全ログ記録が発生する、処理速度が低下します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-dwloader-example"></a>A. Dwloader の単純な例  
次の例では、開始、**ローダー**と必要なオプションのみが選択されています。 その他のオプションは、グローバル構成ファイルから取得*loadparamfile.txt*します。  
  
SQL Server 認証を使用する例です。  
  
```  
--Load over Ethernet  
dwloader.exe -S 10.192.63.148 -U mylogin -P 123jkl -f /configfiles/loadparamfile.txt  
  
--Load over InfiniBand to appliance named MyPDW  
dwloader.exe -S MyPDW-SQLCTL01 -U mylogin -P 123jkl -f /configfiles/loadparamfile.txt  
```  
  
同じの例では、Windows 認証を使用します。  
  
```  
--Load over Ethernet  
dwloader.exe -S 10.192.63.148 -W -f /configfiles/loadparamfile.txt  
  
--Load over InfiniBand to appliance named MyPDW  
dwloader.exe -S MyPDW-SQLCTL01 -W -f /configfiles/loadparamfile.txt  
```  
  
エラー ファイルとソース ファイルの引数を使用する例です。  
  
```  
--Load over Ethernet  
dwloader.exe -U mylogin -P 123jkl -S 10.192.63.148  -i C:\SQLData\AWDimEmployees.csv -T AdventureWorksPDW2012.dbo.DimEmployees -R C:\SQLData\LoadErrors  
```  
  
### <a name="b-load-data-into-an-adventureworks-table"></a>B. AdventureWorks のテーブルにデータを読み込む  
次の例にデータを読み込むバッチ スクリプトの一部は、 **AdventureWorksPDW2012**します。  完全なスクリプトを表示するに付属する aw_create.bat ファイルを開き、 **AdventureWorksPDW2012**インストール パッケージです。 

<!-- Missing link
For more information, see [Install AdventureWorksPDW2012](install-adventureworkspdw2012.md).  
-->

次のスクリプト スニペットは、DimAccount し、DimCurrency テーブルにデータを読み込む dwloader を使用します。 このスクリプトは、イーサネット アドレスを使用しています。 InfiniBand を使用していた場合、サーバーがなります *< appliance_name >* `-SQLCTL01`します。  
  
```  
set server=10.193.63.134  
set user=<MyUser>  
set password=<MyPassword>  
  
set schema=AdventureWorksPDW2012.dbo  
set load="C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwloader.exe"  
set mode=reload  
  
--Loads data into the AdventureWorksPDW2012.dbo.DimAccount table  
--Source data is stored in the file DimAccount.txt,   
--which is in the current directory.  
  
set t1=DimAccount  
%load% -S %server% -E -M %mode% -e Utf16 -i .\%t1%.txt -T %schema%.%t1% -R %t1%.bad -t "|" -r \r\n -U %user% -P %password%   
  
--Loads data from the DimCurrency.txt file into  
--AdventureWorksPDW2012.dbo.DimCurrency  
set t1=DimCurrency  
%load% -S %server% -E -M %mode% -e Utf16 -i .\%t1%.txt -T %schema%.%t1% -R %t1%.bad -t "|" -r \r\n -U %user% -P %password%  
```  
  
DimAccount テーブルに対して DDL を次に示します。  
  
```  
CREATE TABLE DimAccount(  
AccountKey int NOT NULL,  
ParentAccountKey int,  
AccountCodeAlternateKey int,  
ParentAccountCodeAlternateKey int,  
AccountDescription nvarchar(50),  
AccountType nvarchar(50),  
Operator nvarchar(50),  
CustomMembers nvarchar(300),  
ValueType nvarchar(50),  
CustomMemberOptions nvarchar(200))  
with (CLUSTERED INDEX(AccountKey),  
DISTRIBUTION = REPLICATE);  
```  
  
次には、DimAccount.txt DimAccount テーブルに読み込むデータを含む、データ ファイルの例を示します。  
  
```  
--Sample of data in the DimAccount.txt load file.  
  
1||1||Balance Sheet||~||Currency|  
2|1|10|1|Assets|Assets|+||Currency|  
3|2|110|10|Current Assets|Assets|+||Currency|  
4|3|1110|110|Cash|Assets|+||Currency|  
5|3|1120|110|Receivables|Assets|+||Currency|  
6|5|1130|1120|Trade Receivables|Assets|+||Currency|  
7|5|1140|1120|Other Receivables|Assets|+||Currency|  
8|3|1150|110|Allowance for Bad Debt|Assets|+||Currency|  
9|3|1160|110|Inventory|Assets|+||Currency|  
10|9|1162|1160|Raw Materials|Assets|+||Currency|  
11|9|1164|1160|Work in Process|Assets|+||Currency|  
12|9|1166|1160|Finished Goods|Assets|+||Currency|  
13|3|1170|110|Deferred Taxes|Assets|+||Currency|  
```  
  
### <a name="c-load-data-from-the-command-line"></a>C. コマンドラインからデータを読み込む  
例 B のスクリプトは、次の例に示すように、コマンドラインですべてのパラメーターを入力して交換できます。  
  
```  
C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwloader.exe -S <Control node IP> -E -M reload -e UTF16 -i .\DimAccount.txt -T AdventureWorksPDW2012.dbo.DimAccount -R DimAccount.bad -t "|" -r \r\n -U <login> -P <password>  
```  
  
コマンド ライン パラメーターの説明です。  
  
-   *C:\Program files \microsoft SQL Server 並列データ Warehouse\100\dwloader.exe* dwloader.exe のインストールされている場所です。  
  
-   *-S*コントロールのノードの IP アドレスが続きます。  
  
-   *-E* NULL と空の文字列を読み込みを指定します。  
  
-   *-M を再読み込み*をソース データを挿入する前に、変換先テーブルを切り捨てるを指定します。  
  
-   *-e UTF16*リトル エンディアン文字のエンコーディングの種類を使用するソース ファイルを示します。  
  
-   *-i.\DimAccount.txt*データが、現在のディレクトリに存在する DimAccount.txt という名前のファイルを指定します。  
  
-   *-T AdventureWorksPDW2012.dbo.DimAccount*データを受信するテーブルの 3 つの部分名を指定します。  
  
-   *-R DimAccount.bad* DimAccount.bad という名前のファイルに書き込まれます読み込みに失敗した行を指定します。  
  
-   *-t"|"* DimAccount.txt、対象の入力ファイル内のフィールドはパイプ文字で区切られますことを示します。  
  
-   *-r \r\n* DimAccount.txt 内の各行が終わるキャリッジ リターンとライン フィード文字を指定します。  
  
-   *-U < login_name >-p <password>* ログインと、負荷を実行するアクセス許可を持つログインのパスワードを指定します。  
  

<!-- MISSING LINK

## See Also  
[Common Metadata Query Examples](metadata-query-examples.md)  

-->
  
