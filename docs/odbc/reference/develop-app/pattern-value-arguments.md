---
title: パターン値の引数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], pattern value
- pattern value arguments [ODBC]
ms.assetid: 1d3f0ea6-87af-4836-807f-955e7df2b5df
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5befe078127bb526f4fe9a103ec823f2142039f1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="pattern-value-arguments"></a>パターン値の引数
などのいくつかの引数で、カタログ関数、 *TableName*引数**SQLTables**、検索パターンをそのまま使用します。 これらの引数は、検索パターンをそのまま使用 SQL_ATTR_METADATA_ID ステートメント属性が SQL_FALSE; に設定されている場合これらは、この属性が SQL_TRUE に設定されている場合、検索パターンを受け入れない識別子引数です。  
  
 検索パターンの文字は次のとおりです。  
  
-   アンダー スコア (_)、任意の 1 文字を表します。  
  
-   0 個以上の文字の任意のシーケンスを表すパーセント記号 (%)。  
  
-   ドライバー固有の仕様は、% に署名、アンダー スコアを含めるために使用がエスケープ文字とリテラルとエスケープ文字。 ある場合は、エスケープ文字を非特殊文字、エスケープ文字の特別な意味がありません。 エスケープ文字に特殊文字が前にある場合は、特殊文字をエスケープします。 たとえば、"\a"、2 つの文字として取り扱われます"\\"と"a"が"\\%"で特殊でない 1 つの文字「%」として扱われていました。  
  
 エスケープ文字が SQL_SEARCH_PATTERN_ESCAPE オプションで取得される**SQLGetInfo**です。 アンダー スコア、パーセント記号やエスケープ文字の前に引数を受け取るリテラルとしてその文字を含めるように検索パターンにする必要があります。 例を次の表に示します。  
  
|検索パターン|Description|  
|--------------------|-----------------|  
|%A%|文字 A を含むすべての識別子|  
|ABC _|ABC で始まるすべての 4 文字の識別子|  
|ABC\\_|識別子 abc _、エスケープ文字と仮定した場合は、円記号 (\\)|  
|\\\\%|円記号で始まるすべての識別子 (\\)、円記号は、エスケープ文字と仮定した場合|  
  
 検索パターンをそのまま使用する引数の検索パターンの文字をエスケープするために特別な注意を実行する必要があります。 これは特に、下線は識別子でよく使用します。 アプリケーションでよくある間違いは、1 つのカタログ関数から値を取得し、その値を別のカタログ関数の検索パターン引数を渡すにです。 たとえば、アプリケーションの結果から MY_TABLE を設定、テーブル名を取得する**SQLTables**を渡します**SQLColumns** MY_TABLE 内の列の一覧を取得します。 MY_TABLE の列の取得に、代わりに、アプリケーションは MY_TABLE、MY_TABLE MY1TABLE、MY2TABLE、やなどの検索パターンに一致するすべてのテーブルの列を取得します。  
  
> [!NOTE]  
>  ODBC 2 です。*x*ドライバー内の検索パターンをサポートしていません、 *CatalogName*引数**SQLTables**です。 ODBC 3 *.x* SQL_ATTR ODBC_VERSION 環境属性を SQL_OV_ODBC3 に設定されている場合、ドライバーはこの引数での検索パターンを受け入れる; SQL_OV_ODBC2 に設定されている場合、この引数での検索パターンは同意しません。  
  
 検索パターン引数に null ポインターを渡すことです。 その引数の検索を制限しませんつまり、null ポインターと、検索パターン % (任意の文字) は等価です。 ただし、パターンの検索に長さ 0: 長さがゼロの文字列には、有効なポインター: 空の文字列のみと一致する ("") です。
