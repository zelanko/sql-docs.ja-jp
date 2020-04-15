---
title: 相対スクロールと絶対スクロール |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- absolute scrolling [ODBC]
- relative scrolling [ODBC]
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: 3d0ff48d-fef5-4c01-bb1d-a583e6269b66
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae0ed5af8d116a3038b55b1e3d68231154c2a35c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300102"
---
# <a name="relative-and-absolute-scrolling"></a>相対と絶対のスクロール
**SQLFetchScroll**のスクロール オプションのほとんどでは、現在の位置または絶対位置に対して相対的にカーソルを配置します。 **SQLFetchScroll**は、次の行セット、前、最初、最後の行セットのフェッチ、および相対フェッチ (現在の行セットの先頭から行セット*n*行をフェッチ) と絶対フェッチ (行*n*から始まる行セットのフェッチ) をサポートします。 n*が絶対*フェッチで負の値の場合、行は結果セットの末尾からカウントされます。 したがって、行 -1 の絶対フェッチは、結果セット内の最後の行から始まる行セットをフェッチすることを意味します。  
  
 動的カーソルは結果セットに挿入された行と結果セットから削除された行を検出するため、動的カーソルが結果セットの先頭から読み取る以外の特定の数の行を簡単に取得する方法はありません。 また、行番号は行の挿入と削除によって変化するため、動的カーソルでは絶対フェッチはあまり役に立ちません。したがって、同じ行番号を連続してフェッチすると、異なる行が生成される可能性があります。  
  
 **SQLFetchScroll**を使用するアプリケーションは、レポートなどのブロック カーソル機能でのみ、次の行セットをフェッチするオプションのみを使用して、結果セットを 1 回通過する可能性があります。 一方、画面ベースのアプリケーションは、 **SQLFetchScroll**のすべての機能を利用できます。 アプリケーションが行セットのサイズを画面に表示される行数に設定し、画面バッファーを結果セットにバインドすると、スクロール バーの操作を**SQLFetchScroll**の呼び出しに直接変換できます。  
  
|スクロール バーの操作|SQLFetchScroll のスクロール操作|  
|--------------------------|-------------------------------------|  
|1 画面分上へ移動 (PageUp)|SQL_FETCH_PRIOR|  
|1 画面分下へ移動 (PageDown)|SQL_FETCH_NEXT|  
|1 行上へ移動|*フェッチオフセット*が -1 のSQL_FETCH_RELATIVE|  
|1 行下へ移動|*フェッチオフセット*が 1 のSQL_FETCH_RELATIVE|  
|上部にスクロールボックス|SQL_FETCH_FIRST|  
|下のスクロールボックス|SQL_FETCH_LAST|  
|スクロール ボックスを任意の位置に移動|SQL_FETCH_ABSOLUTE|  
  
 このようなアプリケーションでは、スクロール操作の後にスクロール ボックスを配置する必要があります。 現在の行番号については、アプリケーションは現在の行番号を追跡するか、SQL_ATTR_ROW_NUMBER属性を指定して**SQLGetStmtAttr**を呼び出して取得できます。  
  
 カーソル内の行数 (結果セットのサイズ) は、診断ヘッダーのSQL_DIAG_CURSOR_ROW_COUNTフィールドとして使用できます。 このフィールドの値は **、SQL 実行、SQLExecDirect、** または**SQLExecDirect****SQLMoreResult**が呼び出された後にのみ定義されます。 このカウントは、ドライバーの機能に応じて、おおよそのカウントまたは正確なカウントのいずれかになります。 ドライバーのサポートは、カーソル属性情報の種類を使用して**SQLGetInfo**を呼び出し、SQL_CA2_CRC_APPROXIMATEまたはSQL_CA2_CRC_EXACTビットがカーソルの種類に対して返されるかどうかを確認することによって判断できます。  
  
 動的カーソルでは、正確な行数はサポートされません。 その他の種類のカーソルの場合、ドライバーは、正確な行数またはおおよその行数をサポートできますが、両方をサポートすることはできません。 ドライバーが特定のカーソルの種類の正確な行数または近似行数をサポートしていない場合、SQL_DIAG_CURSOR_ROW_COUNT フィールドには、これまでにフェッチされた行の数が含まれます。 ドライバーがサポートする内容に関係なく、SQL_FETCH_LAST*操作*を使用した**SQLFetchScroll**を指定すると、SQL_DIAG_CURSOR_ROW_COUNT フィールドに正確な行数が格納されます。
