---
title: "分離レベルを理解する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c41e23a-da6c-4650-b5fc-b5fe53ba65c3
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8d04a199f44d5a4781ce1bc7b877b4a63d614671
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="understanding-isolation-levels"></a>分離レベルについて
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  各トランザクションでは、別のトランザクションによって行われたリソースまたはデータの変更から特定のトランザクションを分離する際の程度を定義する分離レベルを指定します。 分離レベルは、ダーティ リードやファントム読み取りなど、同時実行の副作用を許可するかどうかという観点で定義されています。  
  
 トランザクション分離レベルでは次の制御を行います。  
  
-   データの読み取り時にロックを獲得するかどうか、要求されるロックの種類。  
  
-   読み取りロックの保持期間。  
  
-   別のトランザクションによって変更された行を参照している読み取り操作で、次のことを行うかどうか。  
  
    -   その行に対する排他ロックが解放されるまでブロックする。  
  
    -   ステートメントまたはトランザクションの開始時に存在していた行の、コミット済みのバージョンを取得する。  
  
    -   コミットされていないデータ変更を参照してください。  
  
 トランザクション分離レベルを選択しても、データ変更を保護するために獲得したロックは影響を受けません。 常にトランザクションは、任意のデータを変更し、設定されたトランザクション分離レベルに関係なく、トランザクションが完了するまでそのロックを保持して排他ロックを取得します。 トランザクション分離レベルでは主に、読み取り操作に対して、他のトランザクションによって行われる変更の影響からの保護レベルを定義します。  
  
 分離レベルが低いほど多くのユーザーが同時にデータにアクセスできるようになりますが、ユーザーに影響が及ぶ可能性がある同時実行の副作用 (ダーティ リードや更新データの喪失など) の種類が多くなります。 反対に、分離レベルが高いほど、ユーザーに影響が及ぶ可能性がある同時実行の副作用の種類は減りますが、必要なシステム リソースが増加し、あるトランザクションによって別のトランザクションがブロックされる状況も多くなります。 適切な分離レベルの選択は、アプリケーションのデータ整合性の要件と各分離レベルのオーバーヘッドとのバランスによって決まります。 最も高い分離レベルの SERIALIZABLE は、トランザクションで読み取り操作が繰り返し実行されるたびに、そのトランザクションで完全に同じデータが取得されることを保証します。このことの実現には、マルチユーザー システムにおいて他のユーザーが影響を受ける可能性が高いロック レベルが適用されています。 最も低い分離レベルは READ UNCOMMITTED ですが、このレベルでは、他のトランザクションによって変更され、まだコミットされていないデータを取得する場合があります。 同時実行のあらゆる副作用が READ UNCOMMITTED では生じる可能性がありますが、読み取りロックやバージョニングは発生しないため、オーバーヘッドはごくわずかです。  
  
## <a name="remarks"></a>解説  
 次の表は、分離レベルごとの同時実行の副作用を示しています。  
  
|[分離レベル]|ダーティ リード|反復不能読み取り|ファントム|  
|---------------------|----------------|-------------------------|-------------|  
|READ UNCOMMITTED|はい|可|はい|  
|読み取りのコミット|不可|はい|はい|  
|REPEATABLE READ|不可|いいえ|はい|  
|スナップショット|不可|いいえ|不可|  
|Serializable|不可|いいえ|不可|  
  
 2 つのトランザクションが同じ行を取得すると、更新内容の喪失が生じる可能性がありますが、この状況を防ぐためには、REPEATABLE READ 以上の分離レベルでトランザクションを実行し、その後で、元の取得した値に基づいて行を更新する必要があります。 2 つのトランザクションが、元の取得した値に基づかずに 1 つの UPDATE ステートメントを使用して行を更新する場合、既定の分離レベル READ COMMITTED では更新データの喪失が発生しません。  
  
 トランザクションの分離レベルを設定するに使用することができます、 [setTransactionIsolation](../../connect/jdbc/reference/settransactionisolation-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。 このメソッドを受け入れる、 **int**に基づいて、次のように接続定数のいずれかの引数として値。  
  
```  
con.setTransactionIsolation(Connection.TRANSACTION_READ_COMMITTED);  
```  
  
 新しいスナップショット分離レベルを使用する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]次のように SQLServerConnection 定数のいずれかを使用することができます。  
  
```  
con.setTransactionIsolation(SQLServerConnection.TRANSACTION_SNAPSHOT);  
```  
  
 また、次のように使用することもできます。  
  
```  
con.setTransactionIsolation(Connection.TRANSACTION_READ_COMMITTED + 4094);  
```  
  
 詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]分離レベルを参照してください"の分離レベルは、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]"で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーでのトランザクションの実行](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  

