---
title: ユニコードアプリケーション |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], compiling as Unicode application
- Unicode [ODBC], functions
- compiling Unicode applications [ODBC]
- functions [ODBC], Unicode functions
ms.assetid: 7986c623-2792-4e77-bfee-c86cbf84f08d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94bd5211c878904453624adb2acd0fe435ebc812
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298948"
---
# <a name="unicode-applications"></a>Unicode アプリケーション
アプリケーションを Unicode アプリケーションとして再コンパイルするには、次の 2 つの方法があります。  
  
-   アプリケーションの Sqlucode.h ヘッダー ファイルに含まれている Unicode **#define**を含めます。  
  
-   コンパイラの Unicode オプションを使用してアプリケーションをコンパイルします。 (このオプションは、コンパイラによって異なります。  
  
 ANSI アプリケーションを Unicode アプリケーションに変換するには、Unicode データを格納して渡すアプリケーションを作成します。 さらに、SQLPOINTER 引数をサポートする関数の呼び出しは、バイト数を使用するように変換する必要があります。  
  
 アプリケーションが Unicode アプリケーションとしてコンパイルされた後、アプリケーションが ODBC API 関数を呼び出す場合 (サフィックスなし)、ドライバー マネージャーは、アプリケーションを Unicode アプリケーションとして認識し、基になるドライバーが Unicode をサポートしている場合は、関数の呼び出しを *(W*サフィックスを持つ) Unicode 関数に変換します。 ANSI アプリケーションがサフィックスを持たない関数呼び出しを行うと、ドライバー マネージャーは、基になるドライバーが ANSI をサポートしている場合は、ANSI に変換します。 アプリケーションとドライバーの両方が同じ文字エンコーディングをサポートしている場合、ドライバー マネージャーは(ANSI アプリケーションの特定の例外を除いて) ドライバーに呼び出しを渡します。  
  
 アプリケーションは、Unicode 関数 *(W*サフィックスを持つ) と ANSI 関数 *(A*サフィックスの有無にかかわらず) の両方を呼び出すことができます。 ユニコードと ANSI 関数呼び出しを混在させることができます。 ただし、カーソル ライブラリを使用する場合は、Unicode 関数と ANSI 関数呼び出しを混在させることはできません。 カーソル ライブラリは、混合ではなく、Unicode または ANSI のいずれかです。  
  
 アプリケーションは、Unicode アプリケーションまたは ANSI アプリケーションとしてコンパイルできるように記述できます。 この場合、文字データ型はSQL_C_TCHARとして宣言できます。 これは、アプリケーションが Unicode アプリケーションとしてコンパイルされた場合にSQL_C_WCHARを挿入するマクロであり、ANSI アプリケーションとしてコンパイルされた場合はSQL_C_CHARを挿入します。 アプリケーションが ANSI であるか Unicode であるかによって、長さ引数のサイズが (文字列データ型の場合) 変わるため、アプリケーション・プログラマーは SQLPOINTER を引数として受け取る関数に注意する必要があります。  
  
 関数は、Unicode のみの関数呼び出し *(W*サフィックスを持つ) として、ANSI のみの関数呼び出し *(A*サフィックスを持つ) として、またはサフィックスを持たない ODBC 関数呼び出しとして呼び出すことができます。 関数の 3 つの形式の引数は同じです。 文字列を指す SQLCHAR\*引数または SQLPOINTER 引数を持つ関数のみが、Unicode 形式と ANSI 形式を必要とします。 **SQLBindCol**や**SQLGetData** (Unicode や ANSI 形式を持たない) などの文字型として宣言できる引数を持つ関数の場合、引数は Unicode 型、ANSI 型、または C 型引数の場合はマクロSQL_C_TCHARとして宣言できます。 詳細については、「 [Unicode データ](../../../odbc/reference/develop-app/unicode-data.md)」を参照してください。  
  
 Unicode ドライバーが使用できない場合でも、アプリケーションを Unicode アプリケーションとして記述できます。 ドライバー マネージャーは、ANSI に Unicode 関数とデータ型をマップします。 実行できる ANSI マッピングへのユニコードには、いくつかの制限があります。 Unicode アプリケーションで動作する Unicode ドライバが存在すると、パフォーマンスが向上し、Unicode から ANSI へのマッピングに固有の制限が解除されます。
