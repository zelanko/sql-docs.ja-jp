---
title: Schema.ini ファイル (テキスト ファイル ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schema.ini file [ODBC]
- text file driver [ODBC], schema.ini file
ms.assetid: 0c4625c4-c730-4984-b430-9051b7bc0451
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 602582886c1eb02e34bad9127e5ab1e55a22a86b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="schemaini-file-text-file-driver"></a>Schema.ini ファイル (テキスト ファイル ドライバー)
テキストのドライバーを使用すると、スキーマ情報ファイルを使用してテキスト ファイルの形式が決まります。 スキーマ情報ファイルが常に Schema.ini という名前し、常にテキスト データ ソースと同じディレクトリ内に保持します。 スキーマ情報ファイルでは、ファイル、列の名前とデータ型情報、およびその他のいくつかのデータの特性の一般的な形式に関する情報を IISAM を提供します。 Schema.ini ファイルは、固定長データにアクセスするために必要では常にします。 文字列テーブルには、DateTime、通貨、または 10 進数データ、またはいつでも、テーブル内のデータの処理より詳細に制御することが含まれている場合、Schema.ini ファイルを使用する必要があります。  
  
> [!NOTE]  
>  レジストリから、Schema.ini からではなく、テキスト ISAM は初期値を取得します。 同じ既定のファイル形式は、すべての新しいテキスト データ テーブルに適用されます。 CREATE TABLE ステートメントによって作成されたすべてのファイルを継承これら同じ既定の形式の値をファイルに値を書式設定を選択して設定される、**テキスト形式の定義**ダイアログ ボックスに\<既定 >、で選択されました。**テーブル** ボックスの一覧です。 Schema.ini 内の値と、レジストリの値が異なる場合、Schema.ini の値によって、レジストリの値が上書きされます。  
  
## <a name="understanding-schemaini-files"></a>Schema.ini ファイルをについてください。  
 Schema.ini ファイルでは、テキスト ファイル内のレコードに関するスキーマ情報を提供します。 Schema.ini の各エントリには、テーブルの 5 つの特性の 1 つを指定します。  
  
-   テキスト ファイルの名前  
  
-   ファイルの形式  
  
-   フィールド名、幅、および種類  
  
-   文字セット  
  
-   特別なデータ型の変換  
  
 次のセクションでは、これらの特性について説明します。  
  
## <a name="specifying-the-file-name"></a>ファイル名の指定  
 Schema.ini の最初のエントリは、常に角かっこで囲まれたテキストのソース ファイルの名前です。 次の例では、Sample.txt ファイルのエントリを示します。  
  
```  
[Sample.txt]  
```  
  
## <a name="specifying-the-file-format"></a>ファイル形式を指定します。  
 **形式**Schema.ini のオプションは、テキスト ファイルの形式を指定します。 Text IISAM は文字で区切られたファイルから自動的に形式を読み取ることができます。 任意の 1 文字は、二重引用符 (") を除く、ファイル内の区切り記号として使用できます。 **形式**Schema.ini の設定は、Windows レジストリ、ファイルごとの設定をオーバーライドします。 次の表に、有効な値の**形式**オプション。  
  
|書式指定子|テーブルの形式|Schema.ini Format ステートメント|  
|----------------------|------------------|---------------------------------|  
|**タブ区切り**|ファイル内のフィールドは、タブで区切られます。|形式 TabDelimited を =|  
|**CSV の区切り**|ファイル内のフィールドはコンマ (コンマ区切り値) で区切られます。|形式 = CSVDelimited|  
|**カスタム区切り**|ファイル内のフィールドは、ダイアログ ボックスへの入力に選択する任意の文字で区切られます。 二重引用符 (") 以外のすべてが許可されている、空白を含むです。|形式区切り記号の = (*カスタム文字*)<br /><br /> -または-<br /><br /> 区切り記号が次のように指定します。<br /><br /> 形式で区切られたに関するページ () を =|  
|**固定長**|ファイル内のフィールドでは、固定長です。|形式 FixedLength を =|  
  
## <a name="specifying-the-fields"></a>フィールドの指定  
 2 つの方法で文字で区切られたテキスト ファイルでフィールド名を指定できます。  
  
-   テーブルの最初の行でフィールド名を含めるし、設定**は**に**True です。**  
  
-   各列番号を指定し、列名とデータ型を指定します。  
  
 番号でそれぞれの列を指定して、列名、データ型、およびファイルの固定長の幅を指定する必要があります。  
  
> [!NOTE]  
>  **は**Schema.ini 上書きの設定、**消えて**Windows レジストリ、ファイルごとに設定します。  
  
 フィールドのデータ型を特定することもできます。 使用して、 **MaxScanRows**した列の型を決定するときに、行の数をスキャンする必要がありますを指定するオプションです。 設定した場合**MaxScanRows**ファイル全体のスキャンを 0 にします。 **MaxScanRows** Schema.ini の設定は、Windows レジストリ、ファイルごとの設定をオーバーライドします。  
  
 次のエントリを示し、こと Microsoft Jet フィールド名を決定する、テーブルの最初の行のデータを使用する必要があります全体のファイルを調べて、データを調べる必要があります使用される型。  
  
```  
ColNameHeader=True  
MaxScanRows=0  
```  
  
 次のエントリは、列番号を使用してテーブル内のフィールドを指定 (**Col * * * n*) 文字で区切られたファイルの省略可能なと固定長のファイルに必要なのオプションです。 例では、2 つのフィールド、10 文字 CustomerNumber テキスト フィールド、および 30 文字 CustomerName テキスト フィールド、Schema.ini のエントリを示しています。  
  
```  
Col1=CustomerNumber Text Width 10  
Col2=CustomerName Text Width 30  
```  
  
 構文 **Col * * * n*は。  
  
```  
  
n=ColumnNametype [#]  
```  
  
## <a name="remarks"></a>解説  
 次の表の各部分の説明、**Col * * * n*エントリです。  
  
|パラメーター|Description|  
|---------------|-----------------|  
|*[ColumnName]*|列のテキストの名前。 列名にスペースが含まれている場合は、二重引用符で囲む必要があります。|  
|*type*|データ型は次のとおりです。<br /><br /> **Microsoft Jet データ型**<br /><br /> bit<br /><br /> Byte<br /><br /> Short<br /><br /> Long<br /><br /> 通貨<br /><br /> 単一<br /><br /> Double<br /><br /> DateTime<br /><br /> テキスト<br /><br /> メモ<br /><br /> **ODBC データ型**Char (テキストと同じ)<br /><br /> Float 型 (Double と同じ)<br /><br /> 整数 (短い形式と同じ)<br /><br /> LongChar (メモ型と同じ)<br /><br /> 日付*日付形式*|  
|**幅**|リテラル文字列値`Width`です。 次の数が、列の幅を指定することを示します (文字で区切られたファイルの省略可能な固定長のファイルに必要)。|  
|*#*|列の幅を指定する整数値 (必要な場合**幅**が指定されている)。|  
  
## <a name="selecting-a-character-set"></a>文字セットの選択  
 2 つの文字セットから選択できます。 ANSI、OEM です。 **CharacterSet** Schema.ini の設定は、Windows レジストリ、ファイルごとの設定をオーバーライドします。 次の例では、文字セットを ANSI に設定する Schema.ini エントリを示します。  
  
```  
CharacterSet=ANSI  
```  
  
## <a name="specifying-data-type-formats-and-conversions"></a>データ型の形式と変換を指定します。  
 Schema.ini ファイルには、データを変換または表示する方法の指定に使用できるいくつかのオプションが含まれています。 次の表には、これらの各オプションが一覧表示します。  
  
|オプション|Description|  
|------------|-----------------|  
|**DateTimeFormat**|日付と時刻を示す書式指定文字列に設定できます。 インポート/エクスポートのすべての日付/時刻フィールドが、同じ形式で処理される場合は、このエントリを指定する必要があります。 午前を除くすべての Microsoft Jet 形式 午後 サポートされます。 書式指定文字列がない場合は、Windows のコントロール パネルの短い日付画像と時間のオプションが使用されます。|  
|**DecimalSymbol**|数値の小数部からの整数を分離するために使用する任意の 1 文字に設定できます。|  
|**NumberDigits**|数値の小数部分の 10 進数字の数を示します。|  
|**NumberLeadingZeros**|1 より小さいと – 1 以上の 10 進数の値が先頭に 0 を含めるかどうかを指定しますこの値は False (先行ゼロなし)、または True です。|  
|**CurrencySymbol**|通貨の値のテキスト ファイルで使用できる通貨記号を示します。 例としては、ドル記号 ($) や Dm です。|  
|**CurrencyPosFormat**|次の値のいずれかに設定できます。<br /><br /> 分離なし ($1) を使用した通貨記号のプレフィックス<br />通貨記号のサフィックスのない (1$)<br />通貨記号のプレフィックスが 1 文字分 (1 ドル)<br />通貨記号のサフィックスが 1 文字分 (1 $)|  
|**CurrencyDigits**|通貨値の小数部分を使用する桁数を指定します。|  
|**CurrencyNegFormat**|次の値のいずれかです。<br /><br /> -   ($1)<br />-   –$1<br />-   $–1<br />-   $1–<br />-   (1$)<br />-   –1$<br />-   1–$<br />-   1$–<br />-   –1 $<br />-   –$ 1<br />-   1 $–<br />-   $ 1–<br />-   $ –1<br />-   1– $<br />-   ($ 1)<br />-   (1 $)<br /><br /> この例は、ドル記号を示していますが、適切な置換する必要があります**CurrencySymbol**実際のプログラム内の値。|  
|**CurrencyThousandSymbol**|数千ものが、テキスト ファイル内の通貨値を区切るために使用できる 1 文字の記号を示します。|  
|**CurrencyDecimalSymbol**|全体を通貨値の小数部から分離に使用される任意の 1 文字に設定できます。|  
  
> [!NOTE]  
>  エントリを省略すると、Windows コントロール パネルの 既定値が使用されます。
