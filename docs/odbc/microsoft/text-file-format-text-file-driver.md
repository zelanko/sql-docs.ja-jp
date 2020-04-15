---
title: テキスト ファイル形式 (テキスト ファイル ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- delimited text lines
- fixed-width text files
- text format [ODBC]
- text file driver [ODBC], text format
ms.assetid: f53cd4b5-0721-4562-a90f-4c55e6030cb9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5801433e0180bb07cb2d09a59db2bb74be012cdf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303093"
---
# <a name="text-file-format-text-file-driver"></a>テキスト ファイルの形式 (テキスト ファイル ドライバー)
ODBC テキスト ドライバーは、区切り文字と固定幅の両方のテキスト ファイルをサポートします。 テキスト ファイルは、オプションのヘッダー行と 0 個以上のテキスト行で構成されます。  
  
 ヘッダー行はテキスト ファイルの他の行と同じ形式を使用しますが、ODBC テキスト ドライバーはヘッダー行エントリをデータではなく列名として解釈します。  
  
 区切りテキスト行には、区切り文字 (コンマ、タブ、またはカスタム区切り文字) で区切られた 1 つ以上のデータ値が含まれます。 ファイル全体で同じ区切り文字を使用する必要があります。 NULL データ値は、行内の 2 つの区切り文字で示され、その間にデータは含めなくなります。 区切り文字で区切られたテキスト行の文字列は、二重引用符 ("" ) で囲むことができます。 区切り記号付き値の前後にブランクを入れても、ブランクは発生しません。  
  
 固定幅テキスト行の各データ入力の幅は、スキーマで指定されます。 NULL データ値はブランクで示されます。  
  
 テーブルのフィールド数は最大 255 個に制限されています。 フィールド名は 64 文字に制限され、フィールドの幅は 32,766 文字に制限されます。 レコードは 65,000 バイトに制限されています。  
  
 テキスト ファイルは、1 人のユーザーに対してのみ開くことができます。 複数のユーザーはサポートされていません。  
  
 プログラマ用に記述された次の文法は、ODBC テキスト ドライバーが読み取ることができるテキスト ファイルの形式を定義します。  
  
|Format|[表記]|  
|------------|--------------------|  
|イタリック体以外|表示されているとおりに入力する必要がある文字|  
|*イタリック 体*|文法の他の場所で定義されている引数|  
|括弧 ([])|省略可能な項目|  
|中かっこ{}( )|相互に排他的な選択肢のリスト|  
|垂直バー (&#124;)|相互に排他的な選択肢を分離する|  
|省略記号 (...)|繰り返し可能なアイテム|  
  
 テキスト ファイルの形式は次のとおりです。  
  
```  
text-file ::=  
   [delimited-header-line] [delimited-text-line]... end-of-file |  
   [fixed-width-header-line] [fixed-width-text-line]... end-of-file  
delimited-header-line ::= delimited-text-line  
delimited-text-line ::=  
   blank-line |  
   delimited-data [delimiter delimited-data]... end-of-line  
fixed-width-header-line ::= fixed-width-text-line  
fixed-width-text-line ::=  
   blank-line |  
   fixed-width-data [fixed-width-data]... end-of-line  
end-of-file ::= <EOF>  
blank-line ::= end-of-line  
delimited-data ::= delimited-string | number | date | delimited-null  
fixed-width-data ::= fixed-width-string | number | date | fixed-width-null  
```  
  
> [!NOTE]  
>  固定幅テキスト ファイル内の各列の幅は、Schema.ini ファイルで指定します。  
  
```  
  
      end-of-line ::= <CR> | <LF> | <CR><LF>  
delimited-string ::= unquoted-string | quoted-stringunquoted-string ::= [character | digit] [character | digit | quote-character]...  
quoted-string ::=  
   quote-character  
   [character | digit | delimiter | end-of-line | embedded-quoted-string]...  
   quote-characterembedded-quoted-string ::=   quote-characterquote-character  
   [character | digit | delimiter | end-of-line]  
   quote-characterquote-characterfixed-width-string ::= [character | digit | delimiter | quote-character] ...  
character ::= any character except:  
   delimiterdigitend-of-fileend-of-linequote-characterdigit ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9  
delimiter ::= , | <TAB> |   
custom-delimitercustom-delimiter ::= any character except:  
   end-of-fileend-of-linequote-character  
```  
  
> [!NOTE]  
>  カスタム区切りテキスト ファイル内の区切り文字は、Schema.ini ファイルで指定されます。  
  
```  
quote-character ::= "  
number ::= exact-number | approximate-number  
exact-number ::= [+ | -] {unsigned-integer[.unsigned-integer] |  
   unsigned-integer. |  
   .unsigned-integer}  
approximate-number ::= exact-number{e | E}[+ | -]unsigned-integer  
unsigned-integer ::= {digit}...  
date ::=  
   mm date-separator dd date-separator yy |  
   mmm date-separator dd date-separator yy |  
   dd date-separator mmm date-separator yy |  
   yyyy date-separator mm date-separator dd |  
   yyyy date-separator mmm date-separator dd  
mm ::= digit [digit]  
dd ::= digit [digit]  
yy ::= digit digit  
yyyy ::= digit digit digit digit  
mmm ::= Jan | Feb | Mar | Apr | May | Jun | Jul | Aug | Sep | Oct | Nov | Dec  
date-separator ::= - | / | .  
delimited-null ::=  
```  
  
> [!NOTE]  
>  区切りファイルの場合、NULL は 2 つの区切り文字の間のデータなしで表されます。  
  
```  
fixed-width-null ::= <SPACE>...  
```  
  
> [!NOTE]  
>  固定幅ファイルの場合、NULL はスペースで表されます。
