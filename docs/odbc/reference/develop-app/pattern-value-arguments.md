---
title: パターン値の引数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], pattern value
- pattern value arguments [ODBC]
ms.assetid: 1d3f0ea6-87af-4836-807f-955e7df2b5df
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0b8e7b7de64d8051118089a54cf14eb45dc96f74
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282382"
---
# <a name="pattern-value-arguments"></a>パターン値の引数
カタログ関数の引数の中には、 **SQLTables**の *"テーブル名"* 引数など、いくつかの引数が検索パターンを受け入れます。 SQL_ATTR_METADATA_ID ステートメント属性が SQL_FALSE に設定されている場合、これらの引数は検索パターンを受け入れます。この属性が SQL_TRUE に設定されている場合、検索パターンを受け入れない識別子引数です。  
  
 検索パターン文字は次のとおりです。  
  
-   任意の 1 文字を表すアンダースコア (_)。  
  
-   0 個以上の文字のシーケンスを表すパーセント記号 (%)。  
  
-   エスケープ文字は、ドライバー固有で、アンダースコア、パーセント記号、およびエスケープ文字をリテラルとして含めるために使用されます。 エスケープ文字が非特殊文字の前にある場合、エスケープ文字は特別な意味を持ちません。 エスケープ文字が特殊文字の前にある場合は、特殊文字をエスケープします。 たとえば、"\a" は "" と "a"\\という 2 文字\\として扱われますが、"%" は非特殊文字の単一文字 "%" として扱われます。  
  
 エスケープ文字は**SQLGetInfo**のSQL_SEARCH_PATTERN_ESCAPE オプションを使用して取得されます。 検索パターンを受け取る引数の中で、アンダースコア、パーセント記号、またはエスケープ文字の前にリテラルとしてその文字を含める必要があります。 例を次の表に示します。  
  
|検索パターン|説明|  
|--------------------|-----------------|  
|%A%|文字 A を含むすべての識別子|  
|ABC_|ABC で始まる 4 つの文字 ID すべて|  
|ABC\\_|エスケープ文字が円記号 (\\) であると仮定すると、識別子はABC_。|  
|\\\\%|バックスラッシュ (\\) で始まるすべての識別子は、エスケープ文字が円記号であると仮定します。|  
  
 検索パターンを受け入れる引数の検索パターン文字をエスケープするには、特別な注意が必要です。 これは、識別子で一般的に使用されるアンダースコア文字に特に当てはまります。 アプリケーションのよくある誤りは、あるカタログ関数から値を取得し、その値を別のカタログ関数の検索パターン引数に渡す場合です。 たとえば、アプリケーションが**SQLTables**の結果セットからテーブル名MY_TABLEを取得し、これを**SQLColumns**に渡してMY_TABLE内の列のリストを取得するとします。 アプリケーションは、MY_TABLEの列を取得する代わりに、MY_TABLE、MY1TABLE、MY2TABLE など、検索パターンMY_TABLEに一致するすべてのテーブルの列を取得します。  
  
> [!NOTE]
>  ODBC 2.*x*ドライバは**SQLTables**の*引数の検索*パターンをサポートしていません。 ODBC 3 *.x*ドライバは、SQL_ATTR_ ODBC_VERSION環境属性がSQL_OV_ODBC3に設定されている場合、この引数の検索パターンを受け入れます。SQL_OV_ODBC2に設定されている場合、この引数の検索パターンは受け入れりません。  
  
 検索パターン引数に null ポインタを渡しても、その引数の検索は制約されません。つまり、NULL ポインターと検索パターン % (任意の文字) が同等です。 ただし、長さがゼロの検索パターン、つまり長さ 0 の文字列への有効なポインターは、空の文字列 ("" ) にのみ一致します。
