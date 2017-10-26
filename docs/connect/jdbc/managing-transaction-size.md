---
title: "トランザクションのサイズを管理する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82900342-bc80-445f-98a4-468a303aae1e
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b333a2aa36c2dd7f2cd0e0065a955455549a813e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="managing-transaction-size"></a>トランザクション サイズの管理
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  トランザクションを扱うときは、トランザクションをできるだけ短くすることが重要です。 既定のモードを有効にするにまたはを使用して無効にする自動コミット、 [setAutoCommit](../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md)メソッド、すべてのアクションがコミットされます。 これは、ほとんどの開発者にとっては最も簡単に扱えるモードです。  
  
 手動トランザクションを使用するときは、トランザクションを可能な限り迅速にコミットする必要があります。 開いているトランザクションを保持していると、他のユーザーがデータにアクセスできなくなります。 たとえば、ロールバックの呼び出しを catch ブロック内に配置し、コミットの呼び出しを finally ブロック内に配置するというプログラミング手法が望ましい場合があります。 ただしこれは、アプリケーションの設計によって異なります。  
  
 トランザクションのサイズを小さくすると、同時実行性が向上します。 たとえば、手動トランザクションを開始し、20,000 行のテーブル内の 10,000 行を変更すると、他のすべてのユーザーは、たとえデータを読み取ろうとしているだけであっても、テーブルの半分にはまったくアクセスできなくなります。 変更する行を 2,000 行に減らせば、テーブルの 90% はアクセス可能になります。  
  
 さらに、アプリケーションでブロックの問題が発生する可能性があり、タイムアウトする必要がある場合は、ロック タイムアウトの設定を使用してください。 使用してこれを行う、 [setLockTimeout](../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)メソッドです。 ロック タイムアウトの既定値は -1 です。これは、ロックを待機している間に無期限にブロックすることを意味します。 ロック タイムアウトを 30 秒に設定すると、別の接続によってブロックされている接続が 30 秒でタイムアウトになります。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによるパフォーマンスと信頼性を向上させる](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  

