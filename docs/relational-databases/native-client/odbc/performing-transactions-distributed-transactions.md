---
title: 分散トランザクションを実行します。マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 588fc51619624b59aef4db1a27deff33d75f8b2a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39561422"
---
# <a name="performing-transactions---distributed-transactions"></a>トランザクションの実行 - 分散トランザクション
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Microsoft 分散トランザクション コーディネーター (MS DTC) により、アプリケーションで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の複数のインスタンスにトランザクションを分散できるようになります。 また、Open Group DTP XA 標準に準拠するトランザクション マネージャーによって管理されるトランザクションに参加させることもできます。  
  
 通常、すべてのトランザクション管理コマンドは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを経由してサーバーに送信されます。 アプリケーションを呼び出すことによってトランザクションを開始する[SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)自動コミット モードをオフにします。 呼び出し、トランザクションを構成する更新プログラムを実行し、アプリケーション[sqlendtran を呼び出してと](../../../relational-databases/native-client-odbc-api/sqlendtran.md)SQL_COMMIT または SQL_ROLLBACK のいずれかのオプションを使用します。  
  
 MS DTC を使用している場合ただし、MS DTC がトランザクション マネージャーとアプリケーションを使用して、不要になった**sqlendtran を呼び出してと**。  
  
 分散トランザクションに参加しているときに 2 番目の分散トランザクションに参加すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは元の分散トランザクションへの参加を解除して、新しいトランザクションに参加します。 詳細についてを参照してください[DTC プログラマーズ リファレンス](http://msdn.microsoft.com/library/ms686108\(VS.85\).aspx)。  
  
## <a name="see-also"></a>参照  
 [トランザクションを実行する&#40;ODBC&#41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
