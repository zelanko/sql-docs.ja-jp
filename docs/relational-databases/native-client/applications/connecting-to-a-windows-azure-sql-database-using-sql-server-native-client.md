---
title: SQL Server Native Client を使用して Windows Azure SQL データベースへの接続 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: native-client|applications
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1dc0139efdaa17cb1046b0661d9e704232a1df4c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32949777"
---
# <a name="connecting-to-a-windows-azure-sql-database-using-sql-server-native-client"></a>SQL Server Native Client を使用した Windows Azure SQL データベースへの接続
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  接続する方法を示すサンプルについては、[!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)]を使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client を参照してください[開発: 操作方法に関するトピック (Windows Azure SQL データベース)](http://msdn.microsoft.com/library/ee621787.aspx)です。  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a>SQL データベースに接続するときの既知の問題  
 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] Native Client を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に接続する場合、次のような既知の問題があります。  
  
-   との接続**SQLBrowseConnect**場合に拒否される可能性が**SQLBrowseConnect**の段階で使用します。  たとえば、最初の通話でドライバー名が送信され、サーバーと資格情報 (ユーザー名とパスワード) が 2 番目の通話で送信されて接続が確立し、データベース名と言語が 3 番目の通話で送信されたとします。  3 番目の通話によって、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は USE ステートメントを発行してデータベースを変更します。 しかし、USE ステートメントは [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] ではサポートされないため、次のエラーが生成されます。  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client でアプリケーションの構築](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
