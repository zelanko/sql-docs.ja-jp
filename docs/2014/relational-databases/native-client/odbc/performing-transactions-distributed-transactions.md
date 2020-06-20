---
title: 分散トランザクションの実行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ec23fd1883749e35e67f888e26bdf031ccf7fb8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055865"
---
# <a name="performing-distributed-transactions"></a>分散トランザクションの実行
  Microsoft 分散トランザクション コーディネーター (MS DTC) により、アプリケーションで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の複数のインスタンスにトランザクションを分散できるようになります。 また、Open Group DTP XA 標準に準拠するトランザクション マネージャーによって管理されるトランザクションに参加させることもできます。  
  
 通常、すべてのトランザクション管理コマンドは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを経由してサーバーに送信されます。 アプリケーションは、自動コミットモードがオフになっている状態で[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)を呼び出すことによってトランザクションを開始します。 次に、アプリケーションは、トランザクションを構成する更新を実行し、SQL_COMMIT または SQL_ROLLBACK オプションを使用して[SQLEndTran](../../native-client-odbc-api/sqlendtran.md)を呼び出します。  
  
 ただし、MS dtc を使用する場合、MS DTC はトランザクションマネージャーになり、アプリケーションは**SQLEndTran**を使用しなくなります。  
  
 分散トランザクションに参加しているときに 2 番目の分散トランザクションに参加すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは元の分散トランザクションへの参加を解除して、新しいトランザクションに参加します。 詳細については、「 [DTC プログラマーズリファレンス](https://msdn.microsoft.com/library/ms686108\(VS.85\).aspx)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;のトランザクションの実行](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
