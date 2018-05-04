---
title: Unicode アプリケーション |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], compiling as Unicode application
- Unicode [ODBC], functions
- compiling Unicode applications [ODBC]
- functions [ODBC], Unicode functions
ms.assetid: 7986c623-2792-4e77-bfee-c86cbf84f08d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1749c6d2e2127af4ff32e97723604dfca82a1c3e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="unicode-applications"></a>Unicode アプリケーション
2 つの方法のいずれかで Unicode アプリケーションとしてアプリケーションを再コンパイルすることができます。  
  
-   Unicode を含む **#define**アプリケーションで、Sqlucode.h ヘッダー ファイルに含まれています。  
  
-   コンパイラの Unicode のオプションを使用してアプリケーションをコンパイルします。 (このオプションに異なるコンパイラによって異なります。)  
  
 Unicode アプリケーションへの ANSI アプリケーションに変換するには、格納および Unicode データを渡すアプリケーションを作成します。 さらに、SQLPOINTER 引数をサポートする関数への呼び出しは、バイト数を使用に変換する必要があります。  
  
 コンパイルした後、アプリケーションは、Unicode アプリケーションとして、アプリケーションが (サフィックス) しない ODBC API 関数を呼び出す場合、ドライバー マネージャーは Unicode アプリケーションとしてアプリケーションを認識し、(、のUnicode関数の関数呼び出しに変換します*W*サフィックス) 場合は、基になるドライバーが Unicode をサポートします。 ANSI アプリケーションは、関数のサフィックスが付いていない呼び出しで、ときに、ドライバー マネージャーに変換します ANSI、基になるドライバーには、ANSI がサポートされている場合。 アプリケーションとドライバーの両方をサポートして、同じ文字エン コード、ドライバー マネージャーはを通じてドライバー (ANSI アプリケーションの特定の例外) への呼び出しを渡します。  
  
 アプリケーションは、両方の Unicode 関数を呼び出すことができます (で、 *W*サフィックス) および ANSI 関数 (有無にかかわらず、 *A*サフィックス)。 Unicode と ANSI 関数の呼び出しを混在させることができます。 カーソル ライブラリを使用する場合は、ただし、Unicode と ANSI の関数呼び出しを混在させることはできません。 カーソル ライブラリは、Unicode または ANSI を混在させないようにします。  
  
 Unicode アプリケーションまたは ANSI アプリケーションとしてそれをコンパイルできるよう、アプリケーションを作成できます。 この場合、文字データ型は、SQL_C_TCHAR として宣言できます。 これは、アプリケーションの場合、Unicode アプリケーションとしてコンパイルや、ANSI アプリケーションとしてコンパイルされている場合、SQL_C_CHAR を挿入、SQL_C_WCHAR を挿入するマクロです。 (文字列データ型) の length 引数のサイズが変化するために、アプリケーション プログラマが、引数としての SQLPOINTER を受け取る関数の注意が必要にする必要があります、アプリケーションは、ANSI または Unicode かどうかによって異なります。  
  
 3 つの方法のいずれかで関数を呼び出すことができます: Unicode 専用の関数呼び出しとして (で、 *W*サフィックス)、ANSI 専用の関数呼び出しとして (で、 *A*サフィックス)、またはサフィックスなし、ODBC 関数呼び出しとして。 関数の 3 つの形式の引数と同じです。 SQLCHAR と関数のみ\*引数または文字列を指す SQLPOINTER 引数は、Unicode と ANSI のフォームを必要とします。 など、文字型として宣言できる引数を持つ関数の**SQLBindCol**または**SQLGetData** (これがない Unicode と ANSI 形式)、引数は、Unicode 型として宣言することができますANSI 型、または C の場合は、型引数、SQL_C_TCHAR マクロです。 詳細については、次を参照してください。 [Unicode データ](../../../odbc/reference/develop-app/unicode-data.md)です。  
  
 動作するために使用可能な Unicode ドライバーがない場合でも、Unicode アプリケーションとしてアプリケーションを記述することができます。 ドライバー マネージャーは、Unicode 関数とデータ型を ANSI にマップされます。 Unicode と ANSI のマッピングを実行できるいくつかの制限があります。 Unicode アプリケーションで動作するための Unicode ドライバーの存在は、パフォーマンスを向上させるし、Unicode ANSI へのマッピングからに固有の制限が削除されます。
