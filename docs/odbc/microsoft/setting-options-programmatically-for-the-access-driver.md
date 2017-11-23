---
title: "プログラムでアクセス ドライバーのオプションの設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Access driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], Access driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
ms.assetid: 1690eb71-0cd3-4c00-9e15-f6a3ac5316dd
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ed08d24f96b66b69bbff409cbc2c9e203526041b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="setting-options-programmatically-for-the-access-driver"></a>プログラムでアクセス ドライバーのオプションの設定
|オプション|Description|方法|  
|------------|-----------------|------------|  
|バッファー サイズ|内部バッファーのサイズをキロバイト単位でディスク間でデータを転送する Microsoft Access で使用されます。 既定のバッファー サイズは、(2048 として表示) 2048 KB です。 256 で割り切れる任意の整数値を入力することができます。|このオプションを動的に設定するへの呼び出しで MAXBUFFERSIZE キーワードを使用[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)です。|  
|Data Source Name|給与担当者など、データ ソースを識別する名前。|このオプションを動的に設定するには、使用、 **DSN**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)です。|  
|データベース|Microsoft Access データ ソースは、選択するか、データベースを作成することがなくを設定できます。 セットアップ時にデータベースが指定されていない場合は、データベース ファイルを選択して、データ ソースに接続するときに、ユーザーが求められます。|このオプションを動的に設定するには、使用、 **DBQ**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)です。|  
|Description|データ ソース内のデータの説明 (オプション)たとえば、「雇用日、給与履歴、およびすべての従業員の現在のレビューします。」|このオプションを動的に設定するには、使用、**説明**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)です。|  
|[Exclusive]|場合、**排他**ボックスが選択されている場合、データベースが排他モードで開き、一度に 1 つだけのユーザーがアクセスできます。 排他モードで実行されている場合、パフォーマンスが向上します。|このオプションを動的に設定するには、使用、**排他**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)です。|  
|ImplicitCommitSync|トランザクションの外部で行われた変更がデータベースに書き込まれる方法を決定します。 この値は"Yes"は、Microsoft Access ドライバーが完了する内部/暗黙のトランザクションでコミットを待機することを意味する初期設定されます。|このオプションが含まれる、**高度なオプションの設定**Microsoft Access ドライバーのダイアログ ボックス。|  
|ページのタイムアウト|(ミリ秒単位) (使用しない場合)、ページが削除される前にバッファーに残っている時間の期間を指定します。 Microsoft Access ドライバー、既定値は 500 ミリ秒 (0.5 秒) です。 このオプションは、ODBC ドライバーを使用するすべてのデータ ソースに適用されます。<br /><br /> ページのタイムアウトは、本質的な遅延のため、0 をすることはできません。 ページのタイムアウトは、その値を下回るページ タイムアウト オプションが設定されている場合でも、本質的な遅延よりも小さくできません。|このオプションを動的に設定するには、使用、 **PAGETIMEOUT**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)です。|  
|[読み取り専用]|読み取り専用で、データベースを指定します。|このオプションを動的に設定するには、使用、 **READONLY**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)です。|  
|システム データベース|Microsoft Access データベースで使用する Microsoft Access のシステム データベースの完全なパスにアクセスします。<br /><br /> クリックして、**システム データベース**ボタンを使用するシステム データベースを選択します。 ODBC Microsoft Access ドライバーには、ユーザー名とパスワードが求められます。 既定の名前は管理者と管理者のユーザーの Microsoft Access での既定のパスワードが空の文字列。<br /><br /> Microsoft Access データベースのセキュリティを強化するには、管理者ユーザーを置き換えるし、管理ユーザーを削除する新しいユーザーを作成または管理ユーザーがアクセスしているオブジェクトを変更します。|このオプションを動的に設定するには、使用、 **SYSTEMDB**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)です。|  
|スレッド|使用する、エンジンのバック グラウンド スレッドの数。 Microsoft Access ドライバーは、この値は、既定値は 3 が、変更することができます。 ユーザーは、大量のデータベース内のアクティビティがある場合は、スレッドの数を増やす可能性があります。<br /><br /> このオプションが含まれる、**高度なオプションの設定**Microsoft Access ドライバーのダイアログ ボックス。|このオプションを動的に設定するには、使用、**スレッド**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)です。|  
|UserCommitSync|Microsoft Access ドライバーが明示的なユーザー定義のトランザクションを非同期的に実行されるかどうかを判断します。 この値は"Yes"は、Microsoft Access ドライバーが完了するユーザー定義のトランザクションのコミットを待機することを意味する初期設定されます。<br /><br /> False には、このオプションを設定すると、マルチ ユーザー環境で予期しない結果があります。|このオプションを動的に設定するには、使用、 **USERCOMMITSYNC**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)です。|
