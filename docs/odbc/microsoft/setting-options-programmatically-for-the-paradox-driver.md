---
title: プログラムによって、Paradox ドライバーのオプションの設定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Paradox driver
- Paradox driver [ODBC], setting options programmatically
- desktop database drivers [ODBC], Paradox driver
- Jet-based ODBC drivers [ODBC], Paradox driver
ms.assetid: 7996d3f8-b5f5-4cac-8a66-fc96a42b603e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5fa8084499f38a7152eb5eeab50010b919f4a06e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904807"
---
# <a name="setting-options-programmatically-for-the-paradox-driver"></a>プログラムによって、Paradox ドライバーのオプションの設定
|オプション|Description|方法|  
|------------|-----------------|------------|  
|ディレクトリ|対象となるディレクトリを設定します。|このオプションを動的に設定するには、使用、 **DEFAULTDIR**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)です。|  
|照合順序|フィールドが並べ替えられたシーケンスです。<br /><br /> シーケンスの有効では、ASCII (既定)、国際化、スウェーデン語、フィンランド語、またはノルウェー語、デンマーク語。|このオプションを動的に設定するには、使用、 **COLLATINGSEQUENCE**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)です。|  
|Description|データ ソース内のデータの説明 (オプション)たとえば、「雇用日、給与履歴、およびすべての従業員の現在のレビューします。」|このオプションを動的に設定するには、使用、**説明**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)です。|  
|[Exclusive]|場合、**排他**ボックスが選択されている場合、データベースが排他モードで開き、一度に 1 つだけのユーザーがアクセスできます。 排他モードで実行されている場合、パフォーマンスが向上します。|このオプションを動的に設定するには、使用、**排他**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)です。|  
|Net スタイル|Paradox データにアクセスするときに使用するネットワーク アクセスのスタイル: か"3*x*"Paradox 3。 *。x*または"4 *。x*"Paradox 4 の *。x*または 5 *。x*です。 3"に設定することができます。*x*"または"4 *。x*"、バージョンが 4 の場合 *。x*または 5 *。x*以外の場合は、バージョンが Paradox 3 の場合 *。x*、スタイルがある必要があります"3 *。x*"です。|このオプションを動的に設定するには、使用、**不正**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)です。|  
|ページのタイムアウト|部分ページ (使用しない場合) が削除される前にバッファーに残っている 1 秒の 1/10 で時間の期間を指定します。 既定値は 600 秒 (60 秒) の部分の 1/10。 このオプションは、ODBC ドライバーを使用するすべてのデータ ソースに適用されます。<br /><br /> ページのタイムアウトは、本質的な遅延のため、0 をすることはできません。 ページのタイムアウトは、その値を下回るページ タイムアウト オプションが設定されている場合でも、本質的な遅延よりも小さくできません。|このオプションを動的に設定するには、使用、 **PAGETIMEOUT**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)です。|  
|[読み取り専用]|読み取り専用で、データベースを指定します。|このオプションを動的に設定するには、使用、 **READONLY**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)です。|  
|ディレクトリを選択します。|アクセスするファイルを含むディレクトリを選択 ダイアログ ボックスが表示されます。<br /><br /> データ ソース ディレクトリを定義すると、最もよく使用されているファイル ディレクトリをどのように指定する場合は、配置されます。 ODBC ドライバーは、このディレクトリを既定のディレクトリとして使用します。 頻繁に使用される場合は、その他のファイルをこのディレクトリにコピーします。 または、ディレクトリの名前で、SELECT ステートメント内のファイル名を修飾することができます。<br /><br /> 選択\*C:\MYDIR\EMP から<br /><br /> またはを使用して新しい既定のディレクトリを指定することができます、 **SQLSetConnectOption**関数 SQL_CURRENT_QUALIFIER オプションを使用します。|このオプションを動的に設定するには、使用、 **DEFAULTDIR**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)です。|  
|ネットワーク フォルダーを選択します。|Pdoxusrs.net ファイルが含まれているために、ロックの paradox を含むディレクトリの完全なパス (Paradox 4 *。x*) または Paradox.net ファイル (Paradox 5 *。x*)。 ディレクトリがこれらのファイルのいずれかにもない場合、Paradox ドライバーは 1 つを作成します。 これらのファイルについては、Paradox ドキュメントを参照してください。<br /><br /> ネットワーク ディレクトリを選択することができます、前に Paradox ユーザー名を入力する必要があります、**ユーザー名**テキスト ボックス。 をクリックして**ネットワーク ディレクトリの選択**ネットワーク ディレクトリを選択します。|このオプションを動的に設定するには、使用、 **PARADOXNETPATH**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)です。|  
|[ユーザー名]|Paradox ユーザー名。 これは、ロックが発生したときに、Paradox ファイルの他のユーザーに表示される名前です。|このオプションを動的に設定するには、使用、 **PARADOXUSERNAME**への呼び出しでキーワード[SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)です。|
