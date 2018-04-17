---
title: '付録 f: ODBC カーソル ライブラリ |Microsoft ドキュメント'
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
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], about cursor library
- ODBC cursor library [ODBC]
- cursor library [ODBC], about cursor library
- cursor library [ODBC]
ms.assetid: a03084df-4e48-48ef-917d-4a3fae48a605
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b7152428dc38f2310cbda7cc70a8a2e4435c5182
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="appendix-f-odbc-cursor-library"></a>付録 f: ODBC カーソル ライブラリ
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 ODBC カーソル ライブラリ (Odbccr32.dll) は、レベル 1 の API への準拠レベルに準拠しているすべてのドライバーのブロックのスクロール可能なカーソルをサポートし、そのアプリケーションやドライバーでの開発者によって再配布できます。 カーソル ライブラリもサポートしている位置指定更新ステートメントと delete ステートメントによって生成される結果セットの**選択**ステートメントです。 これによりは静的カーソルと順方向専用カーソルをサポートしていますが、カーソル ライブラリは多くのアプリケーションのニーズを満たします。 さらに、特に小規模から中規模の結果セット、および適切なカーソルのサポートがないアプリケーションのパフォーマンスは良好を提供できます。  
  
 カーソル ライブラリは、ドライバー マネージャーとドライバーの間にあるダイナミック リンク ライブラリ (DLL) です。 アプリケーションが、関数を呼び出すと、ドライバー マネージャーは、カーソル ライブラリで関数を実行するか、指定されたドライバーで関数を呼び出した関数を呼び出します。 特定の接続は、アプリケーションは、カーソル ライブラリが常に使用になっていること、ドライバーは、スクロール可能なカーソルをサポートしていない場合に使用または使用されないかどうかを指定します。  
  
 カーソル ライブラリは、ドライバーをドライバー マネージャーとして表示されます。 場合は、カーソル ライブラリは、ドライバー マネージャーと ODBC 2 の間に存在します。*x*ドライバー、カーソル ライブラリは、ODBC 2 として表示されます*。x*ドライバー。 ドライバー マネージャーと ODBC 3 の間で、カーソル ライブラリが存在するかどうかは*.x*ドライバー、カーソル ライブラリは、ODBC 3 として表示されます*.x*ドライバー。 カーソル ライブラリでは動作は、両方の ODBC 2 ではサポートされているバインド オフセットを除き、に対して操作してドライバーのバージョンによって異なります。*x*および ODBC 3 *。x*ドライバー。  
  
 ブロック カーソルを実装する**SQLFetch**と**SQLFetchScroll**、カーソル ライブラリを繰り返し呼び出す**SQLFetch**ドライバーにします。 スクロールを実装するのには、メモリ内とディスク ファイルで取得したデータをキャッシュします。 アプリケーションでは、新しい行セットを要求、カーソル ライブラリをドライバーまたはキャッシュから必要なとして取得します。  
  
 Delete ステートメントとを位置指定更新を実装する、カーソル ライブラリを構築、**更新**または**削除**ステートメントを**場所**を示すキャッシュされた句行にバインドされた各列の値です。 位置指定の update ステートメントを実行するとき、カーソル ライブラリは、行セットのバッファー内の値からそのキャッシュを更新します。  
  
 ODBC カーソル ライブラリの詳細については、この付録の次のセクションを参照してください。  
  
-   [ODBC カーソル ライブラリの使用](../../../odbc/reference/appendixes/using-the-odbc-cursor-library.md)  
  
-   [位置指定更新と Delete ステートメントの実行](../../../odbc/reference/appendixes/executing-positioned-update-and-delete-statements.md)  
  
-   [カーソル ライブラリのコード例](../../../odbc/reference/appendixes/cursor-library-code-example.md)  
  
-   [実装に関するメモ](../../../odbc/reference/appendixes/implementation-notes.md)  
  
-   [ODBC カーソル ライブラリのエラー コード](../../../odbc/reference/appendixes/odbc-cursor-library-error-codes.md)
