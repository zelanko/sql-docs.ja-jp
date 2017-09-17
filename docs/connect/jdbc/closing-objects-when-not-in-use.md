---
title: "使用中でないときにオブジェクトを閉じる |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce8f9b35-c761-4b0c-9a46-985eef2c2e0b
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e742eeca533633d1055315a14b1c4f76c061be81
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="closing-objects-when-not-in-use"></a>使用されていないオブジェクトを閉じる
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  オブジェクトを操作するときに[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]、特に[SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)などのオブジェクトのステートメントのいずれかまたは[SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)または[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)、不要になったときに、閉じる方法を使用して、それらに明示的に閉じる必要があります。 これにより、Java 仮想マシンのガベージ コレクターによる処理を待たずに、迅速にドライバーとサーバーのリソースを解放できるため、パフォーマンスが向上します。  
  
 スクロール ロックを使用しているときに、サーバー上で適切な同時実行を維持するためには、オブジェクトを閉じることが特に重要となります。 最後にアクセスしたフェッチ バッファーのスクロール ロックは、結果セットが閉じられるまで保持されます。 同様に、ステートメントの準備されたハンドルは、ステートメントが閉じられるまで保持されます。 複数のステートメントで接続を再利用する場合は、スコープから出る前にステートメントを閉じることで、サーバーが準備されたハンドルを早期にクリーンアップできるようになります。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによるパフォーマンスと信頼性を向上させる](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
