---
title: スレッド サポート (Visual FoxPro ODBC ドライバー) |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77187802bb57a832263ec2070564754e87f21345
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758870"
---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>スレッド サポート (Visual FoxPro ODBC ドライバー)
Visual FoxPro ODBC ドライバーでは、スレッド セーフです。 環境ハンドルへのアクセス (*hen*)、接続ハンドル (*hdbc*)、およびステートメントのハンドル (*hstmt*) を他のプロセスを防ぐために適切なセマフォにラップされていますアクセスと、ドライバーの内部データ構造を変更する可能性があります。  
  
 マルチ スレッド アプリケーションで同期的に実行している関数を取り消すことができます、 *hstmt*呼び出して[SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md)別のスレッドでします。  
  
 ドライバーは、プログレッシブのフェッチを使用する場合は、データをフェッチするのに別のスレッドを使用します。 データ ソースのプログレッシブ フェッチを使用する、**バック グラウンドでデータをフェッチ**チェック ボックスをオン、 [ODBC Visual FoxPro セットアップ ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)BackgroundFetch 属性キーワードを使用して、接続または文字列。 マルチ スレッド アプリケーションからドライバーを呼び出すときに background fetch を使用しないでください。 接続文字列キーワードの属性については、[接続文字列を使用して](../../odbc/microsoft/using-connection-strings.md)を参照してください。  
  
 スレッドの詳細については、 **SQLCancel**を参照してください[SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md)で、 *ODBC プログラマ リファレンス*します。
