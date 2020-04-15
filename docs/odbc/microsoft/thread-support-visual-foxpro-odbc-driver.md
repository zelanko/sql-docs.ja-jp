---
title: スレッドサポート (ビジュアルフォックスプロ ODBC ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- thread support [ODBC]
- Visual FoxPro ODBC driver [ODBC], thread support
- FoxPro ODBC driver [ODBC], thread support
- multithreaded applications [ODBC]
ms.assetid: 0c6abbbc-012b-41aa-bded-5e7e362d015b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2aa19eb233525b5a65ef67fe9903814fc1163177
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303083"
---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>スレッド サポート (Visual FoxPro ODBC ドライバー)
ビジュアル フォックスプロ ODBC ドライバーはスレッド セーフです。 環境ハンドル (*hen*) 、接続ハンドル (*hdbc*) およびステートメント ハンドル (*hstmt*) へのアクセスは、他のプロセスがアクセスし、ドライバーの内部データ構造を変更する可能性を防ぐために、適切なセマフォにラップされます。  
  
 マルチスレッド アプリケーションでは、別のスレッドで[SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md)を呼び出すことによって *、hstmt*上で同期的に実行されている関数をキャンセルできます。  
  
 プログレッシブフェッチを使用する場合、ドライバーは別のスレッドを使用してデータをフェッチします。 データ ソースのプログレッシブフェッチを使用するには[、ODBC Visual FoxPro セットアップ ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)で [**バックグラウンドでデータをフェッチ**する] チェック ボックスをオンにするか、接続文字列で BackgroundFetch 属性キーワードを使用します。 マルチスレッド アプリケーションからドライバーを呼び出すときは、バックグラウンド フェッチを使用しないでください。 接続文字列属性キーワードの詳細については、「[接続文字列の使用](../../odbc/microsoft/using-connection-strings.md)」を参照してください。  
  
 スレッドと**SQLCancel**の詳細については *、ODBC プログラマ リファレンス*の[SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md)を参照してください。
