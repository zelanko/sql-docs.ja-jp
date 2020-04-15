---
title: '付録 F: ODBC カーソル ライブラリ |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], about cursor library
- ODBC cursor library [ODBC]
- cursor library [ODBC], about cursor library
- cursor library [ODBC]
ms.assetid: a03084df-4e48-48ef-917d-4a3fae48a605
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec7982150bfa805c7093ab445400ef5ad1ee070c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292432"
---
# <a name="appendix-f-odbc-cursor-library"></a>付録 F: ODBC カーソル ライブラリ
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 ODBC カーソル ライブラリ (Odbccr32.dll) は、レベル 1 の API 準拠レベルに準拠し、開発者がアプリケーションまたはドライバーを使用して再配布できる任意のドライバーのスクロール可能なブロック カーソルをサポートします。 カーソル ライブラリでは **、SELECT**ステートメントによって生成される結果セットの位置指定更新および削除ステートメントもサポートされます。 静的カーソルと前方専用カーソルのみをサポートしますが、カーソル ライブラリは多くのアプリケーションのニーズを満たします。 また、特に、小規模から中規模の結果セット、およびカーソルサポートが良好でないアプリケーションに対して、良好なパフォーマンスを提供できます。  
  
 カーソル ライブラリは、ドライバー マネージャーとドライバーの間に存在するダイナミック リンク ライブラリ (DLL) です。 アプリケーションが関数を呼び出すと、ドライバー マネージャーは、関数を実行するか、指定されたドライバーで呼び出す、カーソル ライブラリ内の関数を呼び出します。 特定の接続に対して、アプリケーションは、カーソル ライブラリを常に使用するか、ドライバーがスクロール可能なカーソルをサポートしていない場合に使用するか、または使用しないかを指定します。  
  
 カーソル ライブラリは、ドライバー マネージャーにドライバーとして表示されます。 カーソル ライブラリがドライバ マネージャと ODBC *2.x*ドライバの間にある場合、カーソル ライブラリは ODBC *2.x*ドライバとして表示されます。 カーソル ライブラリがドライバ マネージャと ODBC *3.x*ドライバの間にある場合、カーソル ライブラリは ODBC *3.x*ドライバとして表示されます。 カーソル ライブラリで表示される動作は、ODBC *2.x*と ODBC *3.x*の両方のドライバーでサポートされているバインド オフセットを除いて、操作しているドライバーのバージョンによって異なります。  
  
 SQLFetch および**SQLFetchScroll** **SQLFetchScroll**でブロック カーソルを実装するには、カーソル ライブラリは、ドライバーで**SQLFetch**を繰り返し呼び出します。 スクロールを実装するために、メモリとディスク ファイルに取得したデータをキャッシュします。 アプリケーションが新しい行セットを要求すると、カーソル ライブラリは必要に応じて、ドライバーまたはキャッシュから取得します。  
  
 位置指定更新および削除ステートメントを実装するために、カーソル ライブラリは行の各バインド列のキャッシュ値を指定する**WHERE**句を使用して**UPDATE**または**DELETE**ステートメントを作成します。 位置指定更新ステートメントを実行すると、カーソル ライブラリは行セット バッファーの値からキャッシュを更新します。  
  
 ODBC カーソル ライブラリの詳細については、この付録の以下のセクションを参照してください。  
  
-   [ODBC カーソル ライブラリの使用](../../../odbc/reference/appendixes/using-the-odbc-cursor-library.md)  
  
-   [位置指定更新と Delete ステートメントの実行](../../../odbc/reference/appendixes/executing-positioned-update-and-delete-statements.md)  
  
-   [カーソル ライブラリのコード例](../../../odbc/reference/appendixes/cursor-library-code-example.md)  
  
-   [実装に関するメモ](../../../odbc/reference/appendixes/implementation-notes.md)  
  
-   [ODBC カーソル ライブラリのエラー コード](../../../odbc/reference/appendixes/odbc-cursor-library-error-codes.md)
