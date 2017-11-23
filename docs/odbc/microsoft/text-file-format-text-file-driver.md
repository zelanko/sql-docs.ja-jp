---
title: "テキスト ファイルの形式 (テキスト ファイル ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- delimited text lines
- fixed-width text files
- text format [ODBC]
- text file driver [ODBC], text format
ms.assetid: f53cd4b5-0721-4562-a90f-4c55e6030cb9
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0451bf3965e35353d3465cd5bd873954638f2fd
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="text-file-format-text-file-driver"></a>テキスト ファイルの形式 (テキスト ファイル ドライバー)
テキストの ODBC ドライバーでは、両方の区切り記号付き固定幅テキスト ファイルをサポートします。 省略可能なヘッダー行と 0 個以上のテキスト行のテキスト ファイルで構成されます。  
  
 ヘッダー行は、テキスト ファイルの他の行として同じ形式を使用して、テキストの ODBC ドライバーは、データではなく、列名として、ヘッダー行エントリを解釈します。  
  
 区切られたテキスト行には、区切り記号で区切られた 1 つまたは複数のデータ値が含まれています: コンマ、タブ、または独自の区切り記号。 同じ区切り記号は、ファイル全体で使用する必要があります。 データ値 null は、それらの間のデータ行の 2 つの区切り記号で示されます。 区切られたテキスト行の文字列を二重引用符で囲むことができます ("") です。 区切られた値の前後に空白は行われません。  
  
 固定幅テキスト行の場合は、各データ項目の幅は、スキーマで指定されます。 空白では、null データ値が示されます。  
  
 テーブルは、255 個のフィールドの最大数に制限されます。 フィールド名は 64 文字までに制限とフィールドの幅が 32,766 文字に制限されます。 レコードは、65,000 バイトに制限されます。  
  
 テキスト ファイルは、1 人のユーザーに対してのみ開くことができます。 複数のユーザーはサポートされていません。  
  
 次の文章では、プログラマ、用に記述には、テキストの ODBC ドライバーで読み取ることができるテキスト ファイルの形式が定義されています。  
  
|Format|[表記]|  
|------------|--------------------|  
|非表示|文字が示すように入力する必要があります。|  
|*斜体*|文法で別の場所で定義されている引数|  
|角かっこ ()|省略可能な項目|  
|中かっこ ({})|相互に排他的な選択肢の一覧|  
|垂直バー (&#124;)|個別に相互に排他的な選択|  
|省略記号 (...)|項目を 1 回以上繰り返すことができます。|  
  
 テキスト ファイルの形式です。  
  
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
>  固定幅テキスト ファイル内の各列の幅は、Schema.ini ファイルで指定されます。  
  
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
>  Schema.ini ファイルで、カスタム区切りテキスト ファイルの区切り記号が指定されます。  
  
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
>  区切られたファイルの場合、NULL は、次の 2 つの区切り記号の間のデータはありませんで表されます。  
  
```  
fixed-width-null ::= <SPACE>...  
```  
  
> [!NOTE]  
>  固定幅のファイル、null 値はスペースで表されます。
