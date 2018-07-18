---
title: 分散トランザクションの実行 |Microsoft Docs
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
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 04e871ebad4475f4afd388c2a1a0e64fcbc4748d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423681"
---
# <a name="performing-transactions---distributed-transactions"></a>トランザクションの実行 - 分散トランザクション
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Microsoft 分散トランザクション コーディネーター (MS DTC) により、アプリケーションで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の複数のインスタンスにトランザクションを分散できるようになります。 また、Open Group DTP XA 標準に準拠するトランザクション マネージャーによって管理されるトランザクションに参加させることもできます。  
  
 通常、すべてのトランザクション管理コマンドは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを経由してサーバーに送信されます。 アプリケーションが呼び出すことによって、トランザクションを開始[SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)で自動コミット モードをオフにします。 次に、アプリケーションがトランザクションと呼び出しを構成する更新プログラムを実行します[SQLEndTran](../../../relational-databases/native-client-odbc-api/sqlendtran.md)した状態または SQL_ROLLBACK オプションを使用します。  
  
 MS DTC を使用する場合、MS DTC トランザクション マネージャーになり、アプリケーションが使用しなく**SQLEndTran**します。  
  
 分散トランザクションに参加しているときに 2 番目の分散トランザクションに参加すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは元の分散トランザクションへの参加を解除して、新しいトランザクションに参加します。 詳細については、次を参照してください。 [DTC プログラマ リファレンス](http://msdn.microsoft.com/library/ms686108\(VS.85\).aspx)します。  
  
## <a name="see-also"></a>参照  
 [トランザクションを実行する&#40;ODBC&#41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
