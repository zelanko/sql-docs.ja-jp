---
title: "変換に関する規則 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- numeric data type [ODBC], literals
- conversions with numeric literals [ODBC]
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: 89f846a3-001d-496a-9843-ac9c38dc1762
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 06baaaff03f75cbf04da86527a25ea60755a473e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="rules-for-conversions"></a>変換に関する規則
このセクションの規則は、数値リテラルを使用する変換の適用されます。 これらの規則の目的で、次の用語が定義されています。  
  
-   *割り当ての保存:*データベースのテーブルの列にデータを送信するときにします。 呼び出し中に発生したこの**SQLExecute**、 **SQLExecDirect**、および**SQLSetPos**です。 ストアの割り当て中に"target"列を参照するデータベースと「ソース」アプリケーション バッファー内のデータを参照します。  
  
-   *取得割り当て:*アプリケーション バッファーに、データベースからデータを取得するときにします。 呼び出し中に発生したこの**SQLFetch**、 **SQLGetData**、 **SQLFetchScroll**、および**SQLSetPos**です。 取得の割り当て中にアプリケーション バッファーを指す"target"と「ソース」データベースの列を参照しています。  
  
-   *CS:*文字のコピー元の値。  
  
-   *NT:*数値ターゲット内の値。  
  
-   *NS:*数値のソースの値。  
  
-   *CT:*文字ターゲット内の値。  
  
-   正確な数値リテラルの有効桁数: の桁数が含まれています。  
  
-   正確な数値リテラルの小数点以下桁数: 明示または黙示の期間の右側にある数字の数。  
  
-   概数の数値リテラルの有効桁数: の仮数部の有効桁数です。  
  
## <a name="character-source-to-numeric-target"></a>対象の数値を文字のソース  
 文字のコピー元 (CS) から数値のターゲット (NT) への変換の規則を次に示します。  
  
1.  CS を CS 内の先頭または末尾の空白を削除することで得られた値に置き換えます。 CS が、有効でない場合*数値リテラル*、SQLSTATE 22018 (キャストは無効な文字値) が返されます。  
  
2.  CS を後続のゼロ、小数点、またはその両方、小数点の前に伴い、先行ゼロを削除することで得られた値に置き換えます。  
  
3.  NT CS に変換します。 変換結果が有効桁数の損失になる場合は、SQLSTATE 22003 (数値が範囲) が返されます。 変換結果が SQLSTATE 01S07、意味桁の数字が失われる場合 (小数部の切り捨て) が返されます。  
  
## <a name="numeric-source-to-character-target"></a>ターゲットの文字に数値のソース  
 数値のソース (NS) から文字ターゲット (CT) への変換の規則を次に示します。  
  
1.  LT-2-x 文字の長さを使用できます。 取得の割り当て、LT では、この文字セットの null 終端文字のバイト数を引いた数の文字で、バッファーの長さと同じです。  
  
2.  場合:  
  
    -   YP の定義に準拠している最短の文字の文字列と同じで、NS が正確な数値型の場合は、*正確な数値リテラル*YP の小数点以下桁数は、NS、小数点以下桁数と同じと YP の解釈された値になるよう、NS の絶対値。  
  
    -   NS が概数型の場合は、次のように文字列である YP を使用できます。  
  
         場合:  
  
         NS が 0 に等しい場合は、YP は 0 です。  
  
         文字列である、最短の正確な定義に準拠している YSN をできるように*数値リテラル*解釈された値が NS とします。 YSN の長さがある場合より小さい (*精度*+ 1) NS のデータ型の YP YSN を等しきます。  
  
         YP の定義に準拠している最短の文字の文字列は、それ以外の場合、*おおよその数値リテラル*解釈された値がある NS およびがの絶対値*仮数*から成る、1 つ*桁*は '0' ではなく後に、*期間*と*符号なし整数*です。  
  
3.  場合:  
  
    -   NS が 0 未満の場合は、結果である Y を使用します。  
  
         '-' &#124; & #124 です。YP  
  
         場所 ' (& a) #124; &#124;' は、文字列連結演算子です。  
  
         それ以外の場合、等しい YP Y を使用できます。  
  
4.  Y の文字の長さにすることができます。  
  
5.  場合:  
  
    -   等しい場合 LT、CT は Y に設定されます。  
  
    -   場合は LT よりも少ない場合は、CT 設定 Y の右側に拡張する適切な数のスペースがします。  
  
         それ以外の場合 (は > LT)、-2-x に Y の最初の LT 文字をコピー  
  
         場合:  
  
         これは、ストアの割り当てである場合に、SQLSTATE 22001 (文字列データの右側に切り捨てられます) のエラーが返されます。  
  
         検索の割り当ての場合は、警告 SQLSTATE 01004 (文字列データの右側に切り捨てられます) を返します。 コピーの結果 (後続のゼロ) 以外の小数部の桁の損失になる場合、ことがドライバーの定義、次のいずれかが発生するかどうか。  
  
         (1)、ドライバーが適切な小数点以下桁数 (これも 0 にすることができます) を Y で文字列を切り捨てます、-2-x に結果を書き込みます  
  
         (2)、ドライバーが適切な小数点以下桁数 (これも 0 にすることができます) を Y で文字列を丸めます、-2-x に結果を書き込みます  
  
         (3) ドライバーも切り捨てますも丸めますがだけ-2-x に Y の最初の LT 文字をコピー

