---
title: データ ソース ウィザード画面 4 (SQL Server 用 ODBC Driver) |Microsoft ドキュメント
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f53180976b3a4778f687ef8a83d9438ea858c05
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="data-source-wizard-screen-4"></a>データ ソース ウィザード画面 4

SQL Server のメッセージに使用する言語を指定する、文字セットの変換、SQL Server 用 ODBC ドライバーが地域別設定を使用するかどうか。 また、実行時間の長いクエリのログ記録、およびドライバー統計情報の設定を制御することもできます。

## <a name="options"></a>オプション

### <a name="change-the-language-of-sql-server-system-messages-to"></a>[SQL Server のシステム メッセージを以下の言語に変更する]

SQL Server の各インスタンスは、別の言語を使用している (たとえば、英語、スペイン語、フランス語、およびなど) 内の各セットのシステム メッセージの複数のセットを持つことができます。 システム メッセージの複数のセットを含むサーバーに対してデータ ソースを定義する場合、システム メッセージに使用する言語を指定できます。 言語は、一覧でクリックします。 SQL Server で 1 つの言語がインストールされているだけの場合、このオプションは使用できません。

### <a name="use-strong-encryption-for-data"></a>[データに強力な暗号を使用する]

オンにすると、この DSN を使用して確立された接続を介して渡されたデータが暗号化されます。 このチェック ボックスがオフの場合でも、既定では、ログインが暗号化されます。

### <a name="trust-server-certificate"></a>サーバー証明書を信頼します。

このオプションは、該当する場合にのみ**データに対する強力な暗号化を使用して**を有効にします。 選択した場合、サーバーの証明書は、サーバーの適切なホスト名があり、信頼された証明機関が発行するのには検証されません。 

### <a name="perform-translation-for-character-data"></a>[文字データを変換する]

このチェック ボックスを選択すると、SQL Server 用 ODBC driver には Unicode を使用して、クライアント コンピューターと SQL Server の間で送信される ANSI 文字列に変換します。 ODBC ドライバーは、クライアント コンピューターで SQL Server コード ページと Unicode の間で場合がありますに変換します。 これは、SQL Server で使用されるコード ページがクライアント コンピューターで利用可能なコード ページのいずれかを指定する必要があります。

このチェック ボックスがオフの場合、ANSI 文字列の拡張文字は、クライアント アプリケーションとサーバーの間で送信されても変換されません。 クライアント コンピューターが SQL Server コード ページと異なる ANSI コード ページ (ACP) を使用している場合、ANSI 文字列の拡張文字が誤って解釈される可能性があります。 クライアント コンピューターは、同じコード ページを使用して、SQL Server を使用している ACP は、拡張文字が正しく解釈されます。

### <a name="use-regional-settings-when-outputting-currency-numbers-dates-and-times"></a>[出力時の通貨、数値、日付、時刻の形式にはシステムの地域設定を使用する]

ドライバーが文字出力文字列に通貨、数値、日付、時刻の形式にクライアント コンピューターの地域設定を使用するよう指定します。 ドライバーは、データ ソースを介して接続しているユーザーの Windows ログイン アカウントの既定の地域設定を使用します。 このオプションは、データを処理するアプリケーションではなく、データを表示するだけのアプリケーションに選択してください。

### <a name="save-long-running-queries-to-the-log-file"></a>[実行時間が長いクエリを以下のログ ファイルに保存する]

ドライバーがより長く実行されるクエリをログ出力を指定します、**時間の長いクエリ**値。 実行時間の長いクエリのログは、指定されたファイルに記録されます。 ログ ファイルを指定するボックスで、完全なパスとファイル名を入力またはクリックして**参照**を既存のファイル ディレクトリ内を移動して、ログ ファイルを選択します。

### <a name="long-query-time-milliseconds"></a>[保存するクエリの最短所要時間 (ミリ秒)]

実行時間の長いクエリをログに記録するためのしきい値をミリ秒単位で指定します。 このミリ秒単位の時間より実行時間の長いクエリはすべてログに記録されます。

### <a name="log-odbc-driver-statistics-to-the-log-file"></a>[ODBC ドライバーの統計情報ログを以下のログ ファイルに保存する]

統計情報がログに記録されるよう指定します。 統計情報のログは、指定したファイルに記録されます。 ログ ファイルを指定する、ボックスに完全パスとファイル名を入力またはクリックして**参照**を既存のファイル ディレクトリ内を移動して、ログ ファイルを選択します。

統計情報ログはタブで区切られており、タブ区切りのファイルをサポートする Microsoft Excel やその他のアプリケーションで分析できます。

### <a name="connect-retry-count"></a>接続再試行回数

接続試行が失敗の再試行する回数を指定します。

### <a name="connect-retry-interval-seconds"></a>接続の再試行間隔 (秒)

接続再試行間の秒数を指定します。 この操作の詳細については、**接続再試行回数**オプションを参照してください[Windows ODBC ドライバーの接続レジリエンシー](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)です。

### <a name="back"></a>戻る

ウィザードの前のページに戻るには、このボタンをクリックします。

### <a name="finish"></a>完了

クリックすることができる場合、この画面で指定した情報が完了したら、**完了**です。 これであり、ウィザードの他の画面に指定されたすべての属性を使用して DSN が作成され、新しく作成された DSN をテストする機会が与えられます。

## <a name="next-steps"></a>次の手順

[データ ソース ウィザード画面 3](../../../connect/odbc/windows/dsn-wizard-3.md)
