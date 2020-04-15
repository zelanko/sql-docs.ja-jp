---
title: 分散トランザクションを作成する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 05/13/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f21ea9b7146b2907a09688f5189d6d9ae4f3f26a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303706"
---
# <a name="create-a-distributed-transaction"></a>分散トランザクションの作成

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

<!--
The following includes .md file is Empty, as of long before 2019/May/13.
/includes/snac-deprecated.md
-->


分散トランザクションは、さまざまな方法で、さまざまな Microsoft SQL システムに対して作成できます。

## <a name="odbc-driver-calls-the-msdtc-for-sql-server-on-premises"></a>ODBC ドライバーは、オンプレミスの SQL Server の MSDTC を呼び出します。

Microsoft 分散トランザクション コーディネータ (MSDTC)_distribute_を使用すると、アプリケーションは、 の[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]2 つ以上のインスタンスにトランザクションを拡張または分散できます。 分散トランザクションは、2 つのインスタンスが別々のコンピューターでホストされている場合でも機能します。

MSDTC はオンプレミスでインストールされていますが、マイクロソフトの Azure SQL データベース クラウド サービスでは使用できません。

MSDTC は、C++ プログラムが分散トランザクションを管理するときに、オープン データベース接続 (ODBC) 用の SQL Server ネイティブ クライアント ドライバによって呼び出されます。 ネイティブ クライアント ODBC ドライバーには、オープン グループ分散トランザクション処理 (DTP) XA 標準に準拠しているトランザクション マネージャーがあります。 このコンプライアンスは MSDTC で必要です。 通常、すべてのトランザクション管理コマンドは、このネイティブ クライアント ODBC ドライバーを介して送信されます。 順序は次のとおりです。

1. C++ ネイティブ クライアント ODBC アプリケーションは、自動コミット モードをオフにして[SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)を呼び出してトランザクションを開始します。

2. アプリケーションは、コンピュータ A 上の SQL Server X 上のデータを更新します。

3. アプリケーションは、コンピュータ B 上の SQL Server Y 上のデータを更新します。
    - SQL Server Y の更新が失敗した場合は、両方の SQL Server インスタンスでコミットされていない更新がすべてロールバックされます。

4. 最後に、アプリケーションは[SQLEndTran _(1)_](../../../relational-databases/native-client-odbc-api/sqlendtran.md)を呼び出してトランザクションを終了し、SQL_COMMITまたはSQL_ROLLBACKオプションを使用します。

_(1)_ MSDTC は ODBC なしで起動できます。 このような場合、MSDTC がトランザクション マネージャになり、アプリケーションで**SQLEndTran**が使用されなくなります。

### <a name="only-one-distributed-transaction"></a>分散トランザクションは 1 つのみ

C++ ネイティブ クライアント ODBC アプリケーションが分散トランザクションに参加しているとします。 次に、アプリケーションは 2 番目の分散トランザクションに参加します。 この場合、ネイティブ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]クライアント ODBC ドライバーは元の分散トランザクションを残し、新しい分散トランザクションに参加します。

詳細については、「 DTC プログラマ リファレンス 」を[参照してください](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108\(v=vs.85\))。

## <a name="c-alternative-for-sql-database-in-the-cloud"></a>クラウド内の SQL データベースの C# 代替手段

MSDTC は、Azure SQL データベースまたは Azure SQL データ ウェアハウスではサポートされていません。

ただし、C# プログラムで .NET クラス[System.Transactions.TransactionScope](/dotnet/api/system.transactions.transactionscope)を使用することで、SQL データベースの分散トランザクションを作成できます。

### <a name="other-programming-languages"></a>その他のプログラミング言語

以下の他のプログラミング言語では、SQL Database サービスによる分散トランザクションのサポートが提供されない場合があります。

- ODBC ドライバーを使用するネイティブ C++
- トランザクション SQL を使用したリンク サーバー
- JDBC ドライバー

## <a name="see-also"></a>関連項目

[トランザクションの実行 (ODBC)](performing-transactions-in-odbc.md)
