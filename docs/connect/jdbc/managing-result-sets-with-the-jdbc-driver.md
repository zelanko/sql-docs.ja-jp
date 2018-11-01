---
title: JDBC ドライバーによるセットの結果の管理 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9ed5ad41-22e0-4e4a-8a79-10512db60d50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 49bb2f1743675f1ad381b9a5849cc395a5355d42
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837720"
---
# <a name="managing-result-sets-with-the-jdbc-driver"></a>JDBC ドライバーによる結果セットの管理
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  結果セットは、データ ソースから (通常はクエリの結果として) 返された一連のデータを表すオブジェクトです。 結果セットは要求されたデータ要素を保持するための行と列を含み、移動にはカーソルを使用します。 結果セットは更新できます。つまり、変更し、変更内容を元のデータ ソースに反映することができます。 また、結果セットには、基になるデータ ソースの変更に対するさまざまなレベルの応答性を設定できます。  
  
 結果セットの種類はステートメントの作成時に決まります。つまり、[SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) クラスの [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) メソッドへの呼び出しが行われるときです。 結果セットの基本的な役割は、データベースのデータの使用可能な表現を Java アプリケーションに提供することです。 これは通常、結果セットのデータ要素に対する型指定された getter メソッドと setter メソッドによって行われます。  
  
 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースに基づく次の例では、結果セットは [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) クラスの [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) メソッドを呼び出して作成されます。 結果セットのデータは [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) クラスの [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) メソッドを使用して表示されます。  
  
 [!code[JDBC#ManagingResultSets1](../../connect/jdbc/codesnippet/Java/managing-result-sets-with-t_1.java)]  
  
 このセクションのトピックでは、結果セットの使用について、カーソルの種類、コンカレンシー、行ロックなどのさまざまな側面から説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|[説明]|  
|-----------|-----------------|  
|[カーソルの種類について](../../connect/jdbc/understanding-cursor-types.md)|[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] でサポートされるカーソルの種類について説明します。|  
|[コンカレンシー制御について](../../connect/jdbc/understanding-concurrency-control.md)|JDBC ドライバーがコンカレンシー制御をサポートするしくみについて説明します。|  
|[行ロックについて](../../connect/jdbc/understanding-row-locking.md)|JDBC ドライバーが行ロックをサポートするしくみについて説明します。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
