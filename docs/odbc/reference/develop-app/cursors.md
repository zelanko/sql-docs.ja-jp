---
title: カーソル | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- forward-only cursors [ODBC]
- scrollable cursors [ODBC]
- cursors [ODBC], about cursors
- cursors [ODBC]
- fetches [ODBC], cursors
- result sets [ODBC], fetching
- block cursors [ODBC]
ms.assetid: 0b114352-3c63-4d33-9220-182ede90e4aa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da899e4dc47daff03c31277b3edd4d9c642b87cb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305293"
---
# <a name="cursors"></a>カーソル
アプリケーションは *、カーソル*を使用してデータをフェッチします。 カーソルは結果セットとは異なる: 結果セットは特定の検索条件に一致する行のセットであり、カーソルはアプリケーションにそれらの行を返すソフトウェアです。 名前*カーソルは、* データベースに適用される、おそらくコンピュータ端末上の点滅カーソルから発生した。 カーソルが画面上の現在位置を示し、入力した単語が次に表示されるのと同様に、結果セット上のカーソルは結果セット内の現在位置と次に返される行を示します。  
  
 ODBC のカーソル モデルは、埋め込み SQL のカーソル モデルに基づいています。 これらのモデルの間の1つの顕著な違いは、カーソルが開かれる方法です。 埋め込み SQL では、カーソルを使用する前に、カーソルを明示的に宣言してオープンする必要があります。 ODBC では、結果セットを作成するステートメントが実行されると、カーソルが暗黙的にオープンされます。 カーソルがオープンされると、結果セットの最初の行の前にカーソルが置かれます。 埋め込み SQL と ODBC の両方で、アプリケーションが使用を終了した後でカーソルを閉じる必要があります。  
  
 カーソルの特性は異なります。 最も一般的なタイプのカーソル (*前方専用カーソル*と呼ばれる) は、結果セットを順方向にしか進めないです。 前の行に戻るには、アプリケーションはカーソルを閉じて再度開き、結果セットの先頭から必要な行に到達するまで行を読み取る必要があります。 順方向専用カーソルは、結果セットを単一のパスにするための高速なメカニズムを提供します。  
  
 前方スクロールカーソルは、ユーザーがデータを前後にスクロールする画面ベースのアプリケーションでは、あまり役に立ちません。 このようなアプリケーションでは、結果セットを 1 回読み取り、データをローカルにキャッシュし、スクロールを実行することで、前方スクロール カーソルを使用できます。 ただし、この方法は少量のデータでのみ有効です。 より適切な解決策は、結果セットへのランダム アクセスを提供する*スクロール可能なカーソル*を使用することです。 このようなアプリケーションでは、ブロック カーソルと呼ばれるデータを使用して、一度に複数のデータ行をフェッチすることでパフォーマンスを向上*できます。* ブロック カーソルの詳細については、「ブロック カーソルの[使用](../../../odbc/reference/develop-app/using-block-cursors.md)」を参照してください。  
  
 前方スクロール カーソルは ODBC の既定のカーソルの種類であり、以降のセクションで説明します。 ブロック カーソルとスクロール可能なカーソルの詳細については、「[ブロック カーソル](../../../odbc/reference/develop-app/block-cursors.md)と[スクロール可能なカーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)」を参照してください。  
  
> [!IMPORTANT]  
>  **SQLEndTran**を明示的に呼び出すか、自動コミット モードで動作することによってトランザクションをコミットまたはロールバックすると、一部のデータ ソースは接続上のすべてのステートメントのすべてのカーソルを閉じます。 詳細については[、SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明のSQL_CURSOR_COMMIT_BEHAVIORとSQL_CURSOR_ROLLBACK_BEHAVIOR属性を参照してください。
