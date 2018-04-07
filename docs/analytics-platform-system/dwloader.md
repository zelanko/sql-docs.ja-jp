---
title: dwloader Parallel Data Warehouse 用のコマンド ライン ローダー
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: '**dwloader**を既存のテーブルに一括でテーブルの行を読み込む並列データ ウェアハウス (PDW) コマンド ライン ツールです。'
ms.date: 11/04/2016
ms.topic: article
ms.assetid: f79b8354-fca5-41f7-81da-031fc2570a7c
caps.latest.revision: 90
ms.openlocfilehash: 83d04928aa0c8f7fe0156f557466edccc36470dd
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="dwloader-command-line-loader"></a>dwloader のコマンド ライン ローダー
**dwloader**を既存のテーブルに一括でテーブルの行を読み込む並列データ ウェアハウス (PDW) コマンド ライン ツールです。 行を読み込むときに、テーブルの末尾にすべての行を追加することができます (*追加モード*または*fastappend モード*)、新しい行を追加および既存の行を更新 (*upsert モード*)、またはすべてを削除します。既存の読み込みの前に行とし、空のテーブルにすべての行を挿入 (*モードを再読み込み*)。  
  
**データを読み込むためのプロセス**  
  
1.  ソース データを準備します。  
  
    独自の ETL プロセスを使用すると、ロードするソース データを作成できます。 ソース データは、レプリケーション先テーブルのスキーマに合わせてフォーマットされている必要があります。 1 つまたは複数のテキスト ファイルに、ソース データを格納し、テキスト ファイルを読み込み、サーバー上の同じディレクトリにコピーします。 読み込みサーバーについては、次を参照してください[取得と読み込みのサーバーを構成する。](acquire-and-configure-loading-server.md)  
  
2.  読み込みオプションを準備します。  
  
    使用して読み込みオプションを決定します。 構成ファイルに読み込みオプションを格納します。 構成ファイルを読み込み、サーバー上のローカルの場所にコピーします。 **Dwloader**構成オプションは、このトピックで説明されています。  
  
3.  障害のオプションの負荷を準備します。  
  
    方法を決める**dwloader**読み込みに失敗した行を処理します。 読み込みを実行する**dwloader**ステージング テーブルにデータが初めて読み込まれ、変換先テーブルにデータを転送します。 ローダーでは、ステージング テーブルにデータが読み込まれる、読み込みに失敗した行の数を追跡します。 たとえば、正しくフォーマットされていない行は読み込みに失敗します。 失敗した行は、却下ファイルにコピーされます。 既定では、負荷を異なる却下のしきい値を指定していない限り、最初の却下の後に中止します。  
  
4.  インストール**dwloader**です。  
  
    インストールされていない場合は、dwloader の読み込み中のサーバーをインストールします。 

<!-- MISSING LINK
    See [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](install-dwloader-command-line-loader-sql-server-pdw.md). 
--> 
  
5.  実行**dwloader**です。  
  
    読み込みのサーバーにログインし、実行可能ファイルを実行**dwloader.exe**適切なコマンド ライン オプションを使用します。  
  
6.  結果を確認します。  
  
    失敗をチェックすることができます (-r で指定された) ファイルを行を読み込む任意の行が失敗したかどうかを参照してください。 このファイルが空の場合は、すべての行が正常に読み込まれます。 **dwloader**失敗 (拒否された行以外) をステップいずれかの手順をすべてロールバックされますを初期状態には、トランザクションです。  
  
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
}  
```  
  
## <a name="arguments"></a>引数  
**-h**  
ローダーの使用方法に関する簡単なヘルプ情報を表示します。 ヘルプは、その他のコマンド ライン パラメーターが指定されていない場合にのみ表示されます。  
  
**-U** *login_name*  
読み込みを実行する適切なアクセス許可を持つ有効な SQL Server 認証ログインです。  
  
**-P** *password*  
SQL Server 認証のパスワード*login_name*です。  
  
**-W**  
Windows 認証を使用します。 (No *login_name*または*パスワード*必要です)。 

<!-- MISSING LINK
For information about configuring Windows Authentication, see [Security - Configure Domain Trusts](security-configure-domain-trusts.md).  
-->
  
**-f** *parameter_file_name*  
パラメーター ファイルを使用する*parameter_file_name*、コマンド ライン パラメーターの代わりにします。 *parameter_file_name*以外のコマンド ライン パラメーターを含めることができます*user_name*と*パスワード*です。 パラメーターを指定してパラメーター ファイルのコマンドラインで、コマンドラインは、file パラメーターを上書きします。  
  
せずパラメーター ファイルに 1 つのパラメーターが含まれています、 **-** 1 行のプレフィックス。  
  
例 :  
  
`rt=percentage`  
  
`rv=25`  
  
**-S***target_appliance*  
読み込まれたデータを受信する SQL Server PDW アプライアンスを指定します。  
  
*Infiniband 接続*、 *target_appliance* < アプライアンス名 > として指定されて-SQLCTL01 です。 この名前付き接続を構成するのを参照してください。 [InfiniBand ネットワーク アダプターの構成](configure-infiniband-network-adapters.md)です。  
  
イーサネット接続の場合は、 *target_appliance*コントロールのノードのクラスターの IP アドレスです。  
  
省略した場合、dwloader dwloader がインストールされているときに指定された値に既定値です。 

<!-- MISSING LINK
For more information about this install option, see [Install dwloader Command-Line Loader](install-dwloader.md).  
-->
  
**-T** *target_database_name.*[*schema*].*table_name*  
変換先テーブルの 3 部構成の名前。  
  
**-I***source_data_location*  
1 つまたは複数のソース ファイルを読み込む場所です。 各ソース ファイルは、テキスト ファイルまたは gzip で圧縮されているテキスト ファイルにする必要があります。 1 つのソース ファイルは、gzip ファイルごとに圧縮できます。  
  
ソース ファイルの書式を設定します。  
  
-   ソース ファイルは、読み込みオプションに従って書式設定する必要があります。  
  
-   ソース ファイル内の各行には、1 つのテーブル行のデータが含まれています。 ソース データは、レプリケーション先テーブルのスキーマと一致する必要があります。 列の順序およびデータ型が一致する必要がありますもします。 行の各フィールドでは、変換先テーブル内の列を表します。  
  
-   既定では、フィールドは、可変長と区切り記号で区切られました。 区切り記号の種類を指定するには、< variable_length_column_options > コマンド ライン オプションを使用します。 固定長のフィールドを指定するには、< fixed_width_column_options > コマンド ライン オプションを使用します。  
  
ソース データの場所を指定します。  
  
-   ソース データの場所には、ネットワーク パスまたは読み込みサーバー上のディレクトリへのローカル パスを指定できます。  
  
-   ディレクトリ内のすべてのファイルを指定するには、ディレクトリ パスの後に入力してください、* ワイルドカード文字です。  ローダーでは、ソース データの場所にあるすべてのサブディレクトリからのファイルを読み込みません. Gzip ファイル ディレクトリが存在する場合のローダーのエラーです。  
  
-   ディレクトリ内には、一部のファイルを指定するには、文字の組み合わせを使用して、* ワイルドカードです。  
  
1 つのコマンドを使用して複数のファイルを読み込めません。  
  
-   すべてのファイルは、同じディレクトリに存在する必要があります。  
  
-   ファイルは、すべてのテキスト ファイル、gzip のすべてのファイルまたはテキストおよび gzip ファイルの両方の組み合わせにする必要があります。  
  
-   ヘッダー情報をどのファイルも含めることができます。  
  
-   すべてのファイルには、同じ文字のエンコーディングの種類を使用する必要があります。 -E オプションを参照してください。  
  
-   すべてのファイルは、同じテーブルに読み込む必要があります。  
  
-   すべてのファイルは連結および、1 つのファイルは、拒否された行が 1 つの拒否するファイルに移動する場合と同様に読み込まれます。  
  
例 :  
  
-   -i \\\loadserver\loads\daily\\*.gz  
  
-   -i \\\loadserver\loads\daily\\*.txt  
  
-   -i \\\loadserver\loads\daily\monday.*  
  
-   -i \\\loadserver\loads\daily\monday.txt  
  
-   -i \\\loadserver\loads\daily\\*  
  
**-R** *load_failure_file_name*  
読み込みエラーがある場合**dwloader**という名前のファイルのエラー情報は、ロード テストと失敗の説明に失敗した行を格納*load_failure_file_name*です。 このファイルが既に存在する場合、dwloader は既存のファイルを上書きします。 *load_failure_file_name*は最初のエラーが発生したときに作成します。 すべての行が正常に読み込む場合*load_failure_file_name*は作成されません。  
  
**-fh** *number_header_rows*  
先頭に無視する行 (行) の数*source_data_file_name*です。 既定値は 0 です。  
  
<variable_length_column_options>  
オプション、 *source_data_file_name*文字で区切られた可変長列を持ちます。 既定では、 *source_data_file_name*可変長列に ASCII 文字が含まれています。  
  
ASCII ファイルでは、null 値が区切り文字を連続して配置することによって表されます。 たとえば、パイプで区切られたファイルで ("|")、によって null 値が示される"| |"です。 コンマ区切りのファイルで null 値が示されている,「,」です。 さらに、 **-e** (--emptyStringAsNull) オプションを指定する必要があります。 -E の詳細については、以下を参照してください。  
  
**-e** *character_encoding*  
データ ファイルから読み込まれるデータの文字エンコーディング型を指定します。 オプションは (既定値) の ASCII、UTF8、UTF16、または UTF16BE、UTF16 リトル エンディアンあり UTF16BE はビッグ エンディアン。 これらのオプションは、大文字小文字を区別します。  
  
**-t** *field_delimiter*  
内の各フィールド (列)、行区切り記号です。 フィールド区切り記号は、1 つ以上のこれらのエスケープ文字の ASCII または ASCII 16 進値には.  
  
|名前|エスケープ文字|16 進の文字|  
|--------|--------------------|-----------------|  
|タブ|\t|0x09|  
|キャリッジ リターン (CR)|\r|0x0d|  
|ライン フィード (LF)|\n|0x0a|  
|CRLF|\r\n|0x0d0x0a|  
|コンマ|','|0x2c|  
|二重引用符|\\"|0x22|  
|単一引用符|\\'|0x27|  
  
コマンドラインで、パイプ文字を指定するに二重引用符で囲む"|"です。 これにより、コマンド ライン パーサーによって誤って解釈が回避されます。 その他の文字は単一引用符で囲まれます。  
  
例 :  
  
-t "|"  
  
-t ' '  
  
-t 0x0a  
  
-t \t  
  
-t '~|~'  
  
**-r** *row_delimiter*  
元のデータ ファイルの行ごとに区切り記号です。 行区切り記号は、1 つまたは複数の ASCII 値です。  
  
キャリッジ リターン (CR)、改行 (LF)、またはタブ文字を区切り記号として指定するには、エスケープ文字 (\r、\n、\t) またはその 16 進値 (0 x、09、0 d) を使用できます。 区切り文字として他の特殊文字を指定するには、16 進数の値を使用します。  
  
CR-LF + の例:  
  
-r \r\n  
  
-r 0x0d0x0a  
  
CR の例:  
  
-r \r  
  
-r 0x0d  
  
LF の例:  
  
-r \n  
  
-r 0x0a  
  
LF は、Unix の必要があります。 CR は、Windows の必要があります。  
  
**-s** *string_delimiter*  
文字列データの区切り記号は、テキスト区切りの入力ファイルのフィールドを入力します。 文字列の区切り記号は、1 つまたは複数の ASCII 値です。  文字として指定できます (例: s *) または 16 進値 (例:-s 0x22、二重引用符の)。  
  
例 :  
  
-s *  
  
-s 0x22  
  
< fixed_width_column_options>  
固定長列を含むソース データ ファイルのオプションです。 既定では、 *source_data_file_name*可変長列に ASCII 文字が含まれています。  
  
– E は UTF8 ときに、固定幅列はサポートされていません。  
  
**-w** *fixed_width_config_file*  
パスと各列の文字数を指定する構成ファイルの名前。 すべてのフィールドを指定する必要があります。  
  
このファイルは、読み込みサーバー上に存在する必要があります。 パスは、UNC、相対パスまたは絶対パスにすることができます。 それぞれの線に*fixed_width_config_file*その列の 1 つの列と文字数の名前が含まれています。 次のように、1 列あたり 1 つの行があるし、ファイル内の順序が先テーブルの順序と一致する必要があります。  
  
*column_name*=*num_chars*  
  
*column_name*=*num_chars*  
  
固定幅の構成ファイルの例:  
  
SalesCode=3  
  
SalesID 10 を =  
  
内の行を例*source_data_file_name*:  
  
230Shirts0056  
  
320Towels1356  
  
前の例では、最初に読み込まれた行が SalesCode = '230' および SalesID 'Shirts0056' を = です。 読み込まれた 2 つ目の行が SalesCode をある = '320' および SaleID = 'Towels1356' です。  
  
先頭および末尾の固定幅モードで、スペースやデータの型変換を処理する方法については、次を参照してください。[データ型の dwloader の変換規則](dwloader-data-type-conversion-rules.md)です。  
  
**-e** *character_encoding*  
データ ファイルから読み込まれるデータの文字エンコーディング型を指定します。 オプションは (既定値) の ASCII、UTF8、UTF16、または UTF16BE、UTF16 リトル エンディアンあり UTF16BE はビッグ エンディアン。 これらのオプションは、大文字小文字を区別します。  
  
– E は UTF8 ときに、固定幅列はサポートされていません。  
  
**-r** *row_delimiter*  
元のデータ ファイルの行ごとに区切り記号です。 行区切り記号は、1 つまたは複数の ASCII 値です。  
  
キャリッジ リターン (CR)、改行 (LF)、またはタブ文字を区切り記号として指定するには、エスケープ文字 (\r、\n、\t) またはその 16 進値 (0 x、09、0 d) を使用できます。 区切り文字として他の特殊文字を指定するには、16 進数の値を使用します。  
  
CR-LF + の例:  
  
-r \r\n  
  
-r 0x0d0x0a  
  
CR の例:  
  
-r \r  
  
-r 0x0d  
  
LF の例:  
  
-r \n  
  
-r 0x0a  
  
LF は、Unix の必要があります。 CR は、Windows の必要があります。  
  
**-D** { **ymd** | ydm | mdy | myd |  dmy | dym | *custom_date_format* }  
入力ファイルで月 (m)、日 (d)、および datetime のすべてのフィールドの年 (y) の順序を指定します。 既定の順序は、ymd です。 同じソース ファイルの複数の注文形式を指定するには、–-dt オプションを使用します。  
  
ymd | dmy  
ydm と dmy は、同じ入力形式を使用できます。 両方には、日付の末尾または先頭にある年ができるようにします。 たとえば、両方とも**ydm**と**dmy**日付の書式、入力ファイルの 2013-02-03 または 02-03-2013 がある可能性があります。  
  
ydm  
のみのデータ型 datetime および smalldatetime の列に ydm として書式設定の入力を読み込むことができます。 Ydm 値は、datetime2、日付、または datetimeoffset データ型の列に読み込むことができません。  
  
mdy  
により、mdy <month> <space> <day> <comma><year>です。  
  
1975 年 1 月 1 日の mdy 入力データの例:  
  
-   1975 年 1 月 1 日  
  
-   75 Jan 01日  
  
-   年 1 月/1/75  
  
-   01011975  
  
myd  
ファイルの例の年 3 月入力 04,2010: 03-2010-04、3/2010/4  
  
dym  
2010 年 3 月 4 日、ファイルの例の入力: 04-2010-03、3/4/2010  
  
*custom_date_format*  
*custom_date_format*カスタムの日付形式は、(例:/mm/dd/yyyy) 旧バージョンとの互換性を保つのために含まれているとします。 dwloader のでは、カスタムの日付形式、enfoce されません。 代わりに、カスタムの日付形式を指定する**dwloader** ymd、ydm、mdy、myd、dym、dmy の対応する設定に変換されます。  
  
たとえば、– D 年/月/日を指定すると dwloader のすべての日付の月の最初に、注文を入力し、日、および年 (mdy) しが必要です。 2 文字か月、2 桁の日、およびカスタムの日付の形式で指定された 4 桁の年を強制することはできません。 ここでは、日付の形式は、– D/mm/dd/yyyy ときに、入力ファイルで日付を形式指定できる方法の例: 01/02/2013、Jan.02.2013、2013 年 1 月 2 日  
  
包括的な書式設定については、次を参照してください。[データ型の dwloader の変換規則](dwloader-data-type-conversion-rules.md)です。  
  
**-dt** *datetime_format_file*  
各 datetime 形式がという名前のファイルで指定された*datetime_format_file*です。 コマンドラインのパラメーターとは異なり、空白を含むファイルのパラメーターを二重引用符で囲んでいない必要があります。 データを読み込むよう datetime 形式を変更することはできません。 元のデータ ファイルとコピー先のテーブルで、対応する列には、同じ形式がある場合があります。  
  
各行には、コピー先のテーブルとその datetime 形式で列の名前が含まれています。  
  
例 :  
  
`LastReceiptDate=ymd`  
  
`ModifiedDate=dym`  
  
**-d** *staging_database_name*  
ステージング テーブルを格納するデータベース名。 既定値は、コピー先のテーブルのデータベースでは、-t オプションで指定されたデータベースです。 詳細については、ステージング データベースを使用して、次を参照してください。[ステージング データベースを作成する](staging-database.md)です。  
  
**-M** *load_mode_option*  
追加、upsert、またはデータを再読み込みするかどうかを指定します。 既定のモードを追加します。  
  
append  
ローダーでは、変換先テーブル内の既存の行の末尾に行を挿入します。  
  
fastappend  
ローダーは、変換先テーブルの既存の行の末尾に、一時テーブルを使用せず、直接、行を挿入します。 fastappend には、複数のトランザクションが必要です (– m) オプション。 Fastappend を使用する場合、ステージング データベースを指定できません。 読み込みプロセスにより、失敗または中止負荷からの復旧を処理する必要があり、fastappend のロールバックは行われません。  
  
upsert **-K**  *merge_column* [ ,...*n* ]  
ローダーでは、SQL Server マージ ステートメントを使用して、既存の行を更新し、新しい行を挿入します。  
  
-K オプションは、マージの基に列を指定します。 これらの列は、一意の行を表す必要があります、マージのキーを形成します。 コピー先のテーブルに主キーが存在する場合、行が更新されます。 コピー先のテーブルに主キーが存在しない場合、行が追加されます。  
  
ハッシュ分散テーブルでは、主キーがするか、ディストリビューション列を含める必要があります。  
  
レプリケートされたテーブルの場合は、主キーは、1 つまたは複数の列の組み合わせです。 これらの列は、アプリケーションのニーズに合わせて指定します。  
  
複数の列は、コンマ、スペースなしでスペースを含むコンマ区切りや単一引用符で囲まれたにする必要があります。  
  
ソース テーブル内の 2 つの行のマージ キーの値が一致する場合は、それぞれの行が同一でなければなりません。  
  
再読み込み  
ソース データを挿入する前に、ローダーは、変換先テーブルを切り捨てます。  
  
**-b** *batchsize*  
Microsoft サポートによってのみの使用を推奨*batchsize* DMS をコンピューティング ノード上の SQL Server のインスタンスを実行する一括コピーの SQL Server のバッチ サイズです。  ときに*batchsize*を指定すると、SQL Server PDW は各負荷に対して動的に計算されるバッチ読み込みサイズよりも優先されます。  
  
SQL Server 2012 PDW から始まり、コントロールのノードは、既定では各読み込みのバッチ サイズを動的に計算します。 この自動計算は、メモリ サイズ、ターゲット テーブルの種類、対象テーブルのスキーマ、負荷の種類、ファイルのサイズ、およびユーザーのリソースのクラスなどのいくつかのパラメーターに基づいています。  
  
たとえば、負荷モードに FASTAPPEND があり、ユーザーがテーブルにクラスター化列ストア インデックスは、SQL Server PDW は既定値は 1,048, 576、バッチ サイズを使用して、行グループが終了になるようにしようと直接ロードして、列ストアを経由せず、デルタ ストアです。 メモリが 1,048, 576 のバッチ サイズを許可していない場合、dwloader は小さなバッチ サイズを選択します。  
  
負荷の種類が FASTAPPEND の場合、 *batchsize*それ以外の場合、テーブルにデータを読み込む対象*batchsize*ステージング テーブルにデータを読み込むには適用されます。  
  
<reject_options>  
ローダーにより、読み込みエラーの数を決定するためのオプションを指定します。 読み込みエラーがしきい値を超えた場合、ローダーは停止し、すべての行をコミットできません。  
  
**-rt** { **value** | percentage }  
指定するかどうかは、*reject_value*で、 **-rv** *reject_value*オプションは、リテラル (値) または行数、エラー (割合) の割合がします。 既定値は、値です。  
  
割合オプションは、リアルタイム - rs オプションに基づいて間隔で発生する計算です。  
  
たとえば、100 行および 25 の読み込みにローダー試行が失敗する、75 が成功する場合は、25% は障害発生率にします。  
  
**-rv** *reject_value*  
負荷を停止する前に使用できるように数または行の却下のパーセンテージを指定します。 **-Rt**オプションどう*reject_value*行数または行の割合を表します。  
  
既定値*reject_value*は 0 です。  
  
-Rt 値に使用する場合、ローダーは、拒否された行の数が reject_value を超えた場合に負荷を停止します。  
  
応答時間の割合で使用する場合、ローダー比率を計算、間隔で (-rs オプション)。 そのため、失敗した行の割合を超える場合*reject_value*です。  
  
**-rs** *reject_sample_size*  
使用される、`-rt percentage`増分割合チェックを指定するオプションです。 たとえば、reject_sample_size が 1000 の場合は、ローダー比率が計算されます、失敗した行の後 1000 行をロードしようとしました。 各追加の 1000 行の読み込みを試みた後、失敗した行の割合が再計算します。  
  
**-c**  
Char、nchar、varchar、および nvarchar のフィールドの右側と左側からの空白文字を削除します。 空の文字列に空白文字だけを含む各フィールドに変換します。  
  
例 :  
  
'' に切り捨て '  
  
'    abc     ' gets truncated to 'abc'  
  
– C を使用する場合、E、– E の操作が最初に発生します。 空白文字のみを含むフィールドは、空の文字列と NULL に変換されます。  
  
**-E**  
空の文字列を NULL に変換します。 既定では、これらの変換を実行できません。  
  
**-m**  
読み込みの 2 番目のフェーズに複数のトランザクション モードを使用します。ときに、分散型のテーブルにステージング テーブルからデータを読み込んでいます。  
  
**– M**、SQL Server PDW を実行し、並列読み込みをコミットします。 これにより、読み込みモードでは、既定値よりもはるかに高速に実行が、トランザクションの安全ではありません。  
  
せず**– m**、SQL Server PDW を実行し、各コンピューティング ノード内でのディストリビューションと同時にコンピューティング ノード間で負荷を逐次的にコミットします。 このメソッドは、複数のトランザクション モードよりも遅くなりますが、トランザクション セーフです。  
  
**-m**は省略可能です*追加*、*再読み込み*、および*upsert*です。  
  
**-m** fastappend が必要です。  
  
**-m**レプリケートされたテーブルでは使用できません。  
  
**-m**読み込みの 2 番目のフェーズにのみ適用されます。 最初の読み込みフェーズ; には適用されません。ステージング テーブルにデータを読み込んでいます。  
  
独自のロード プロセスによって、失敗または中止負荷からの復旧を処理する必要が複数のトランザクション モードでのロールバックは行われません。  
  
使用することをお勧め**– m**データを失わずに回復することができるように、空のテーブルに読み込む場合にのみです。 読み込みエラーから回復する: 変換先テーブルを削除、負荷の問題を解決する、変換先テーブルを再作成して負荷を再実行します。  
  
**-N**  
ターゲット アプライアンスが信頼された機関から有効な SQL Server PDW の証明書を確認します。 使用して、データがされていないことを確認が攻撃者によって盗ま、不正な場所に送信します。 証明書は、アプライアンスの既にインストールする必要があります。 証明書をインストールする唯一のサポートされている方法は、Configuration Manager ツールを使用してインストールするアプライアンス管理者がします。 かどうかはするが不明であるかどうか、アプライアンス インストールされている信頼された証明書をアプライアンスの管理者に依頼します。  
  
**-se**  
空のファイルの読み込みをスキップします。 これも空に gzip ファイルを圧縮解除をスキップします。  
  
## <a name="return-code-values"></a>リターン コードの値  
0 (成功) またはその他の整数値 (失敗)  
  
コマンド ウィンドウまたはバッチ ファイルで使用して`errorlevel`リターン コードを表示します。 以下に例を示します。  
  
```  
dwloader  
echo ReturnCode=%errorlevel%  
if not %errorlevel%==0 echo Fail  
if %errorlevel%==0 echo Success  
```  
  
PowerShell を使用してを使用して`$LastExitCode`です。  
  
## <a name="permissions"></a>権限  
読み込み権限とコピー先のテーブルに適用可能な権限 (INSERT、UPDATE、DELETE) が必要です。 ステージング データベース (一時テーブルの作成) に対する作成アクセス許可が必要です。 ステージング データベースを使用しない場合は、転送先データベースに作成する権限が必要です。 

<!-- MISSING LINK
For more information, see [Grant permissions to load data](grant-permissions-to-load-data.md).  
-->
  
## <a name="general-remarks"></a>全般的な解説  
Dwloader を使用して読み込むときのデータ型変換については、次を参照してください。[データ型の dwloader の変換規則](dwloader-data-type-conversion-rules.md)です。  
  
パラメーターには、1 つ以上のスペースが含まれている場合は、二重引用符を含むパラメーターを囲みます。  
  
インストール場所からローダーを実行する必要があります。 Dwloader の実行可能ファイルでは、アプライアンスにプリインストールされており、C:\Program files \microsoft SQL Server データ Warehouse\DWLoader ディレクトリにあります。  
  
パラメーター ファイルで指定されているパラメーターを上書きすることができます (-f オプション) コマンド ライン パラメーターとして指定することができます。  
  
ローダーの複数のインスタンスを同時に実行することができます。 ローダーのインスタンスの最大数は、事前に構成されておよびは変更できません。 

<!-- MISSING LINK
For the maximum number of loads per appliance, see [Minimum and Maximum Values](minimum-maximum-values.md)  
-->
  
読み込まれたデータは、多かれ少なかれソースの場所により、アプライアンス上の領域を必要があります。 ディスクの消費量を推定するためのデータのサブセットでテストのインポートを行うことができます。  
  
**Dwloader**は、トランザクションのプロセスとはロールバックが実行に失敗した場合に、一括読み込みが正常に完了した後にロールバックできません。 アクティブなをキャンセルする**dwloader**プロセスは、CTRL + C キーを入力します。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
必要があります、データベースの LOG_SIZE よりも小さくして、すべての同時読み込みの合計サイズをお勧め同時に発生したすべての負荷の合計サイズは、LOG_SIZE の 50% 未満です。 このサイズの制限を実現するためには、複数のバッチに大きな負荷を分割できます。 LOG_SIZE の詳細については、次を参照してください[データベースの作成。](../t-sql/statements/create-database-parallel-data-warehouse.md)  
  
1 つの負荷のコマンドを使用して複数のファイルを読み込むときに、拒否されたすべての行が同じ拒否するファイルに書き込まれます。 拒否するファイルでは、拒否された行を含む入力ファイルは表示されません。  
  
空の文字列を区切り記号として指定しないでください。 行区切り記号として空の文字列を使用すると、負荷が失敗します。 負荷が区切り記号を無視し、引き続き既定値を使用する、列区切り記号として使用されるときに"|"、列区切り記号として。 空の文字列は無視されます、文字列の区切り記号として使用されるときにされ、既定の動作が適用されます。  
  
## <a name="locking-behavior"></a>ロック動作  
**dwloader**ロック動作によって異なります、 *load_mode_option*です。  
  
-   **追加**– 追加の推奨されると、最も一般的なオプションです。 ステージング テーブルにデータを読み込みますを追加します。 ロックは、以下で詳しく説明します。  
  
-   **高速追加**– ExclusiveUpdate テーブル ロック、最終テーブルに直接読み込み、ステージング テーブルを使用しない唯一のモードは、高速追加します。  
  
-   **再読み込み**– 再読み込みがステージング テーブルにデータを読み込み、ステージング テーブルと、最終テーブルの両方に対する排他ロックが必要です。 同時操作は、再読み込みはお勧めしません。  
  
-   **upsert** – Upsert をステージング テーブルにデータを読み込むし、最終テーブルにステージング テーブルから、マージ操作を実行します。 Upsert には、最終テーブルに排他ロックは不要です。 アップサートを使用する場合、パフォーマンスが異なる場合があります。 環境内で動作をテストします。  
  
### <a name="locking-behavior"></a>ロック動作  
**Append モード ロック**  
  
追加 (– m 引数を使用して) マルチ トランザクション モードで実行することができますが、トランザクションの安全ではありません。 そのための追加 (– m 引数を使用) せずに、トランザクション操作として使用する必要があります。 残念ながら、最終的な INSERT SELECT 操作で、トランザクション モードが現在約 6 倍よりも低い複数のトランザクション モードです。  
  
Append モードでは、2 つのフェーズでデータが読み込まれます。 第 1 フェーズでは、ステージング テーブルに同時に (断片化が発生することができます)、ソース ファイルからデータを読み込みます。 フェーズ 2 では、最終テーブルにステージング テーブルからデータを読み込みます。 2 番目のフェーズを実行、 **INSERT INTO.選択 WITH (TABLOCK)**操作します。 追加モードのログ記録の動作を使用する場合と、次の表は、最終テーブルにロックの動作を示しています。  
  
|テーブル型|複数のトランザクション<br />モード (-m)|テーブルが空です。|サポートされている同時実行|ログ記録|  
|--------------|-----------------------------------|------------------|-------------------------|-----------|  
|ヒープ|はい|[ユーザー アカウント制御]|はい|最小|  
|ヒープ|はい|いいえ|はい|最小|  
|ヒープ|いいえ|可|いいえ|最小|  
|ヒープ|いいえ|いいえ|いいえ|最小|  
|Cl|はい|[ユーザー アカウント制御]|いいえ|最小|  
|Cl|はい|いいえ|はい|Full|  
|Cl|いいえ|可|いいえ|最小|  
|Cl|いいえ|いいえ|はい|Full|  
  
上記の表に示す**dwloader** append モード、ヒープまたはクラスター化インデックス (CI) テーブル、トランザクションで複数のフラグの有無を読み込むと、空のテーブルまたは空でないテーブルへの読み込みを使用します。 ロックと、負荷のような組み合わせでは、それぞれの動作をログ記録は、テーブルに表示されます。 たとえばのフェーズ append モードとは異なる (2) の読み込みとテーブル PDW テーブルに排他ロックを作成する必要があるマルチ トランザクション モードを使用せず、クラスター化インデックスと、空にログ記録は最小限に抑える。 これは、顧客がいないできる (2 番目) の段階とクエリを同時に空のテーブルに読み込むことを意味します。 ただし、PDW では、テーブルに排他ロックは発行されませんと空でないテーブルに同じ構成を読み込むときに、同時実行が可能です。 残念ながら、完全ログ記録が発生したプロセスのパフォーマンスの低下します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-dwloader-example"></a>A. Dwloader の単純な例  
次の例では、開始、**ローダー**と必要なオプションのみが選択されています。 その他のオプションは、グローバル構成ファイルから取得されます*loadparamfile.txt*です。  
  
SQL Server 認証を使用する例です。  
  
```  
--Load over Ethernet  
dwloader.exe -S 10.192.63.148 -U mylogin -P 123jkl -f /configfiles/loadparamfile.txt  
  
--Load over InfiniBand to appliance named MyPDW  
dwloader.exe -S MyPDW-SQLCTL01 -U mylogin -P 123jkl -f /configfiles/loadparamfile.txt  
```  
  
同じ例の Windows 認証を使用します。  
  
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
次の例にデータを読み込むバッチ スクリプトの一部である**AdventureWorksPDW2012**です。  表示するには、完全なスクリプトに付属している aw_create.bat ファイルを開く、 **AdventureWorksPDW2012**インストール パッケージです。 

<!-- Missing link
For more information, see [Install AdventureWorksPDW2012](install-adventureworkspdw2012.md).  
-->

次のスクリプトのスニペットは、DimAccount し、DimCurrency テーブルにデータを読み込む dwloader を使用します。 このスクリプトは、イーサネット アドレスを使用しています。 InfiniBand、使用していた場合、サーバーがなります*< appliance_name >*`-SQLCTL01`です。  
  
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
  
データ ファイル、DimAccount テーブルに読み込むデータを含む DimAccount.txt の例を次に示します。  
  
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
例 B のスクリプトは、次の例で示すように、コマンドラインですべてのパラメーターを入力して交換できます。  
  
```  
C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwloader.exe –S <Control node IP> -E –M reload –e UTF16 -i .\DimAccount.txt –T AdventureWorksPDW2012.dbo.DimAccount –R DimAccount.bad –t "|" –r \r\n –U <login> -P <password>  
```  
  
コマンド ライン パラメーターの説明:  
  
-   *C:\Program files \microsoft SQL Server 並列データ Warehouse\100\dwloader.exe* dwloader.exe のインストールされている場所です。  
  
-   *-S*コントロールのノードの IP アドレスが続きます。  
  
-   *-E* NULL と空の文字列をロードすることを指定します。  
  
-   *-M が再読み込み*をソース データを挿入する前に、変換先テーブルを切り捨てるを指定します。  
  
-   *-e UTF16*リトル エンディアン文字エンコーディングの種類を使用するソース ファイルを示します。  
  
-   *-i.\DimAccount.txt*データが、現在のディレクトリに存在する DimAccount.txt という名前のファイルを指定します。  
  
-   *-T AdventureWorksPDW2012.dbo.DimAccount* specifies the 3-part name of the table to receive the data.  
  
-   *-R DimAccount.bad* DimAccount.bad という名前のファイルに書き込まれます読み込みに失敗した行を指定します。  
  
-   *– t"|"* DimAccount.txt、対象の入力ファイル内のフィールドが、パイプ文字で区切られたことを示します。  
  
-   *-r \r\n* DimAccount.txt 内の各行をキャリッジ リターンを終了し、ライン フィード文字を指定します。  
  
-   *-U < login_name >-p <password>* ログインと、読み込みを実行するアクセス許可を持つログインのパスワードを指定します。  
  

<!-- MISSING LINK

## See Also  
[Common Metadata Query Examples](metadata-query-examples.md)  

-->
  
