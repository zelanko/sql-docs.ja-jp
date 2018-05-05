---
title: ODBC プログラマ&#39;リファレンス |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], reference
ms.assetid: b33c3c43-ae66-44a3-be17-9cd82624dd96
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b570b616ee14b8fd1f70b755a134be72045b1114
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-programmer39s-reference"></a>ODBC プログラマ&#39;リファレンス
*ODBC プログラマ リファレンス*次のセクションが含まれています。  
  
-   [ODBC 3.8 新](../../odbc/reference/what-s-new-in-odbc-3-8.md)Windows 8 SDK で追加された新しい ODBC の機能を一覧表示します。  
  
-   [ODBC プログラムのサンプル](../../odbc/reference/sample-odbc-program.md)ODBC のプログラム例を示します。  
  
-   [ODBC の概要](../../odbc/reference/introduction-to-odbc.md)構造化照会言語と ODBC、および ODBC インターフェイスの概念についての簡単な履歴を提供します。  
  
-   [アプリケーションの開発](../../odbc/reference/develop-app/developing-applications.md)ODBC インターフェイスとそれを実装するドライバーを使用するアプリケーションの開発に関する情報が含まれています。  
  
-   [インストールと構成の ODBC ソフトウェア](../../odbc/reference/install/installing-and-configuring-the-odbc-software.md)インストールとセットアップ DLL の関数参照に関する情報を提供します。  
  
-   [ODBC ドライバーの開発](../../odbc/reference/develop-driver/developing-an-odbc-driver.md)ドライバーの記述に関する情報が含まれています。  
  
-   [API リファレンス](../../odbc/reference/syntax/odbc-reference.md)構文とセマンティクス情報すべての ODBC 関数について説明します。  
  
-   [ODBC 付録](../../odbc/reference/appendixes/odbc-appendixes.md)技術的な詳細が含まれており、ODBC エラー コード、データ型、および SQL の文法のテーブルを参照します。  
  
## <a name="working-with-the-odbc-documentation"></a>ODBC のドキュメントの操作  
 ODBC インターフェイスは、C プログラミング言語で使用するために設計されています。 ODBC インターフェイスの使用が 3 つの領域にまたがる: SQL ステートメント、ODBC 関数呼び出し、および C プログラミングします。 このドキュメントには、次の前提としています。  
  
-   C プログラミング言語の知識。  
  
-   一般的な DBMS の知識と SQL 熟知します。  
  
 次の表記規則が使用されます。  
  
|形式|使用目的|  
|------------|--------------|  
|選択 * から|大文字の使用は、SQL ステートメント、マクロ名、およびオペレーティング システム コマンド レベルで使用される用語を示します。|  
|`RETCODE SQLFetch(hdbc)`|コマンドラインのサンプルとプログラム コードの固定幅フォントを使用します。|  
|*argument*|斜体の単語は、プログラム引数をユーザーまたはアプリケーションする必要があります提供または情報は、word の強調を示します。|  
|**SQLEndTran**|太字では、構文を示すように、関数名を含む正確に入力する必要あることを示します。|  
|&#124;|垂直バーは、構文の行で相互に排他的な 2 つの選択肢を区切ります。|  
|[...]|省略記号を引数繰り返せることを示します何回か。|  
|」をご覧ください。 と呼ばれています。 」をご覧ください。|3 つのドットの列では、前の行のコードの継続タスクを示します。|  
  
## <a name="about-the-code-examples"></a>コード例について  
 このガイドのコード例は、わかりやすくするためだけに設計されています。 ODBC 原則のデモンストレーションに主に書き込まれる、ため効率も確保されているわかりやすくするためです。 さらに、コードのセクションでは全体は、わかりやすくするため省略された場合があります。 これらには、非 ODBC 関数 (これらの関数が名前が"SQL"で始まらない) とほとんどのエラー処理の定義が含まれます。  
  
 すべてのコード例を使用して ANSI 文字列と同一のデータベースのスキーマの冒頭に示した[カタログ関数](../../odbc/reference/develop-app/catalog-functions.md)です。  
  
## <a name="recommended-reading"></a>推奨トピック  
 SQL の詳細については、次の標準を使用できます。  
  
-   データベース言語 — SQL 整合性機能強化、ANSI、1989 ANSI X3.135 1989 にします。  
  
-   データベースの言語: SQL: ANSI X3H2 と ISO/IEC JTC1/SC21/WG3 9075:1992 (SQL 92)。  
  
-   Open Group、データ管理: 構造化照会言語 (SQL), Version 2 (、the Open Group 1996)。  
  
 標準とベンダー固有の SQL ガイドだけでなく、多くの書籍が SQL をについて説明を含みます。  
  
-   日付、Darwen もに、C. J.: *SQL 標準的なガイド*(、Addison-wesley、1993)。  
  
-   誰、Sandra L.、Darnovsky、Marcy、および弓、Judith S.:*実践的な SQL マニュアル*(、Addison-wesley、1989)。  
  
-   Groff、James R. と Weinberg、Paul N.: *SQL を使用して*(◆ セグ: McGraw-丘、1990)。  
  
-   グルーバー、Martin: *SQL を理解する*(Sybex、1990)。  
  
-   Hursch、回線のモジュラー ジャック L. と Carolyn J.: *SQL、構造化照会言語*(タブ ブック、1988)。  
  
-   メルトン、Jim、および Simon、Alan R.:*新しい SQL を理解する: 完全なガイド*(更にパブリッシャーの場合、1993)。  
  
-   Pascal、Fabian: *SQL とリレーショナルの基礎*() (& T ブック、1990)。  
  
-   Trimble、J. Harvey、Jr. および Chappell、David: *Visual SQL 入門*(Wiley、1989)。  
  
-   Van der Lan、Rick F.: *SQL の概要*(、Addison-wesley、1988)。  
  
-   Vang、Soren: *SQL およびリレーショナル データベース*(Microtrend ブック、1990)。  
  
-   Viescas、John: *SQL クイック リファレンス ガイド*(Microsoft Corp.、1989)。  
  
 トランザクション処理の詳細についてを参照してください。  
  
-   グレーの場合、J. n を付けます。 最も、Andreas:*トランザクション処理: 概念および手法*(更にパブリッシャーの場合、1993)。  
  
-   Hackathorn、Richard D.: *Enterprise データベース接続*(Wiley & 人の息子、1993)。  
  
 呼び出しレベルのインターフェイスの詳細については、次の標準を使用できます。  
  
-   Open Group*データ管理: SQL 呼び出しレベルのインターフェイス (CLI) C451* (Open Group、1995)。  
  
-   ISO/IEC 9075-3:1995、呼び出しレベルのインターフェイス (SQL/CLI)。  
  
 ODBC に関する詳細については、ブックの数が利用可能。  
  
-   Geiger、Kyle: *ODBC 内*(Microsoft Press®、1995)。  
  
-   Gryphon という、Robert、Charpentier、Luc、Oelschlager、Jon、Shoemaker、Andrew、Jim、クロスと Lilley、アルバート W.: *ODBC 2 を使用して*(Que、1994)。  
  
-   Johnston、Tom および先生、マーク: *ODBC 開発者向けガイド*(Howard W. Sam & 会社、1994)。  
  
-   北、Ken:*マルチ DBMS の Windows プログラミング: C++、Visual Basic、ODBC、OLE 2 およびツールを使用して、プロジェクトの DBMS* (◆ セグ: & 人の息子, inc., 1995)。  
  
-   Stegman、Michael O.、Signore、Robert、および Creamer、John: *ODBC ソリューションでのオープン データベース コネクティビティ分散環境*(McGraw-丘、1995)。  
  
-   就く、Keith: *ODBC 2 を使用して*(Que、1994)。  
  
-   Whiting、課金内容:*学ぶ 21 日以内に ODBC* (Howard W. Sam & 会社、1994)。
