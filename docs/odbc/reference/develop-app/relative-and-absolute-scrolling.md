---
title: "相対パスと絶対スクロール |Microsoft ドキュメント"
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
- absolute scrolling [ODBC]
- relative scrolling [ODBC]
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: 3d0ff48d-fef5-4c01-bb1d-a583e6269b66
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cf5155a44827adb972881da17ac2bc05d92a0cd4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="relative-and-absolute-scrolling"></a>相対パスと絶対スクロール
スクロール オプションのほとんど**SQLFetchScroll**相対的な現在の位置または絶対位置にカーソルを置きます。 **SQLFetchScroll** 、次のフェッチをサポートしています前に、最初と最後の行セット、相対パスとしてもフェッチとして (行セットをフェッチ *n* 現在の行セットの先頭からの行) と絶対フェッチ (fetch、。行セットの行で始まる *n* )。 場合 *n* は行が結果セットの最後から数えられます絶対フェッチで負の値。 したがって、– 1 の行の絶対フェッチは結果セットの最後の行で始まる行セットをフェッチすることです。  
  
 動的カーソルは挿入および動的カーソルの速度が低下する可能性が、結果セットの先頭から読み取り以外の特定の番号に対応する行を取得する簡単な方法がないように、結果セットから削除された行を検出します。 さらに、絶対フェッチではありません非常に役に動的カーソル行番号を変更するように行が挿入および削除します。そのため、同じ行の数を連続してフェッチすることで得られる別の行にします。  
  
 使用するアプリケーション**SQLFetchScroll**そのブロックにのみレポートなどのカーソル機能は、1 回、結果セットを通過する可能性がありますオプションのみを使用して、次の行セットをフェッチします。 スクリーン ベースのアプリケーションでは、その一方で、活用することのすべての機能**SQLFetchScroll**です。 スクロール バー操作を直接の呼び出しを変換できる場合は、アプリケーションでは、画面に表示される行数を行セットのサイズに設定しを結果セットに、画面バッファーをバインド、 **SQLFetchScroll**です。  
  
|スクロール バーの操作|SQLFetchScroll のスクロール操作|  
|--------------------------|-------------------------------------|  
|1 画面分上へ移動 (PageUp)|SQL_FETCH_PRIOR|  
|1 画面分下へ移動 (PageDown)|SQL_FETCH_NEXT|  
|1 行上へ移動|指定した SQL_FETCH_RELATIVE *FetchOffset* – 1 に等しい|  
|1 行下へ移動|指定した SQL_FETCH_RELATIVE *FetchOffset*を 1 に等しい|  
|上部にあるスクロール ボックス|SQL_FETCH_FIRST|  
|下部のスクロール ボックス|SQL_FETCH_LAST|  
|スクロール ボックスを任意の位置に移動|SQL_FETCH_ABSOLUTE|  
  
 このようなアプリケーションも、現在の行番号と行の数が必要ですが、スクロール操作の後のスクロール ボックスを配置する必要があります。 現在の行番号、アプリケーションかを追跡できます、現在の行番号または呼び出し**SQLGetStmtAttr** SQL_ATTR_ROW_NUMBER 属性を取得するとします。  
  
 結果のサイズであると、カーソル内の行の数は、設定、診断のヘッダーの SQL_DIAG_CURSOR_ROW_COUNT フィールドとして使用できます。 このフィールドの値が後でだけ定義されている**SQLExecute**、 **SQLExecDirect**、または**SQLMoreResult**が呼び出されています。 この数には、カウントの概数またはドライバーの機能によって、正確な数のいずれかを指定できます。 ドライバーのサポートを呼び出すことによって判断**SQLGetInfo**カーソルの属性の種類の情報と SQL_CA2_CRC_APPROXIMATE または SQL_CA2_CRC_EXACT ビットがカーソルの型に対して返されるかどうかをチェックします。  
  
 動的カーソルの正確な行の数がサポートされていることはありません。 他の種類のカーソルでは、ドライバーは、真数または概数値の行カウントが両方をサポートできます。 ドライバーには、正確なもおおよそがサポートされている場合は、行カウントの種類の特定のカーソルに対して、SQL_DIAG_CURSOR_ROW_COUNT フィールドが、これまでにフェッチされる行の数が含まれています。 どのようなドライバーをサポートするのに関係なく**SQLFetchScroll**で、*操作*SQL_FETCH_LAST のにより SQL_DIAG_CURSOR_ROW_COUNT フィールドに正確な行の数を格納します。

