---
title: 分散トランザクションの作成 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fc61ad955be287faad20289245ca4520efcd4bbd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67913172"
---
# <a name="create-a-distributed-transaction"></a>分散トランザクションを作成します。

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

<!--
The following includes .md file is Empty, as of long before 2019/May/13.
/includes/snac-deprecated.md
-->

[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

分散トランザクションは、さまざまな Microsoft SQL システムのさまざまな方法で作成できます。

## <a name="odbc-driver-calls-the-msdtc-for-sql-server-on-premises"></a>ODBC ドライバーでは、MSDTC を呼び出して、オンプレミス SQL Server の

Microsoft 分散トランザクション コーディネーター (MSDTC) により、拡張するアプリケーションまたは_配布_の 2 つ以上のインスタンス間でトランザクション[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 分散トランザクションは、2 つのインスタンスが別のコンピューターにホストされている場合でも機能します。

MSDTC では、Microsoft SQL Server、オンプレミスのインストールされますが、Microsoft の Azure SQL Database のクラウド サービスに対しては使用できません。

MSDTC を呼び出して、SQL Server Native Client ドライバー Open Database Connectivity (ODBC) の場合、C++プログラムは、分散トランザクションを管理します。 Native Client ODBC ドライバーが、トランザクション マネージャーで、開いているグループに分散トランザクション処理 (DTP) XA 標準に準拠します。 MSDTC では、このコンプライアンスが必要です。 通常、すべてのトランザクション管理コマンドは、この Native Client ODBC ドライバーを介して送信されます。 シーケンスは次のとおりです。

1. C++ Native Client ODBC アプリケーションでは、呼び出すことによってトランザクションが開始されます[SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)、自動コミット モードをオフにします。

2. アプリケーションがコンピューター A で SQL Server の一部のデータを更新します。

3. アプリケーションがコンピューター B 上で SQL サーバー Y 上のデータを更新します。
    - SQL サーバー Y の更新プログラムが失敗した場合、両方の SQL Server インスタンスでコミットされていないすべての更新プログラムはロールバックされます。

4. 最後に、アプリケーションが呼び出すことによってトランザクションを終了[SQLEndTran _(1)_ ](../../../relational-databases/native-client-odbc-api/sqlendtran.md)、した状態または SQL_ROLLBACK オプションを使用します。

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

_(1)_ ODBC せず、MSDTC を呼び出すことができます。 このような場合は、MSDTC、トランザクション マネージャーになり、アプリケーションが使用しなく**SQLEndTran**します。

### <a name="only-one-distributed-transaction"></a>1 つだけの分散トランザクション

たとえば次に示す、 C++ Native Client ODBC アプリケーションが分散トランザクションに参加しています。 次に、アプリケーションは、2 番目の分散トランザクションに参加します。 ここで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを選択して、元の分散トランザクションになり、新しい分散トランザクションに参加します。

詳細についてを参照してください[DTC プログラマーズ リファレンス](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108\(v=vs.85\))。

## <a name="c-alternative-for-sql-database-in-the-cloud"></a>C#代わりに、クラウドで SQL database

MSDTC は、Azure SQL Database または Azure SQL Data Warehouse のサポートされていません。

で分散トランザクションを SQL Database を作成するただし、C#プログラムは、.NET クラスを使用して[System.Transactions.TransactionScope](/dotnet/api/system.transactions.transactionscope)します。

### <a name="other-programming-languages"></a>他のプログラミング言語

以下、他のプログラミング言語は、SQL Database サービスでの分散トランザクションのサポートを提供しない可能性があります。

- ネイティブC++ODBC ドライバーを使用します。
- TRANSACT-SQL を使用してリンク サーバー
- JDBC ドライバー

## <a name="see-also"></a>関連項目

[トランザクションの実行 (ODBC)](performing-transactions-in-odbc.md)
