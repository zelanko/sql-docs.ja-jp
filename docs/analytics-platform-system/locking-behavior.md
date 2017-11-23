---
title: "ロック動作 (SQL Server PDW)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c55c636e-b767-4a0c-8184-be991a10801f
caps.latest.revision: "27"
ms.openlocfilehash: 6f4b213942db85b9e7171d11d6b88512d3ad7779
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="locking-behavior"></a>ロック動作
SQL Server PDW は、トランザクションの整合性を確保して、複数のユーザーが同時にデータにアクセスするときに、データベースの一貫性を維持するために、ロックを使用します。  
  
## <a name="Basics"></a>ロックの基礎  
**モード**  
  
SQL Server PDW は、次の 4 つのロック モードをサポートします。  
  
[Exclusive]  
書き込み、排他ロックの完了を保持しているトランザクションまでロックされたオブジェクトからの読み取りや排他ロックを禁止します。 排他ロックが有効なときにいずれかのモードの他のロックが許可されません。 たとえば、DROP TABLE と CREATE DATABASE は、排他ロックを使用します。  
  
Shared  
共有ロックは、影響を受けるオブジェクトの排他ロックの開始を禁止されていますが、他のすべてのロック モードを許可します。 たとえば、SELECT ステートメント共有ロックを開始してしたがってでは複数のクエリを同時に、選択したデータにアクセスできますが、SELECT ステートメントが完了するまでは、読み取られるレコードの更新を回避します。  
  
ExclusiveUpdate  
ExclusiveUpdate ロックはロックされたオブジェクトへの書き込みを禁止されていますが、共有ロックを使用して読み取りを許可するがします。 ExclusiveUpdate ロックが有効なときに他のロックが許可されません。 たとえば、データベースのバックアップおよびデータベースの復元は、排他的な更新ロックを使用します。  
  
SharedUpdate  
SharedUpdate ロックは、排他的と ExclusiveUpdate のロック モードを禁止しで共有および SharedUpdate ロック モードは、オブジェクトでします。 SharedUpdate でオブジェクトを変更制限は行われません読み取りアクセス権を変更中にします。 たとえば、挿入し、更新プログラムでの SharedUpdate ロックを使用します。  
  
**リソース クラス**  
  
オブジェクトの各クラスでロックが保持されますデータベース、スキーマ、オブジェクト (テーブル、ビュー、または手順)、アプリケーション (内部使用)、EXTERNALDATASOURCE、EXTERNALFILEFORMAT および SCHEMARESOLUTION (データベース レベルのロック取得、作成中に変更、または。削除するスキーマのオブジェクトやデータベース ユーザー)。 これらのオブジェクト クラスは、の object_type 列に示される[sys.dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)です。  
  
## <a name="Remarks"></a>全般的な解説  
ロックは、データベース、テーブル、またはビューに適用できます。  
  
SQL Server PDW は、構成可能な分離レベルを実装していません。 ANSI 標準で定義されている READ_UNCOMMITTED 分離レベルをサポートします。 ただし、した READ_UNCOMMITTED で操作が実行される読み取り、ごく限られたブロッキング操作実際に発生するか、またはシステムに競合する可能性です。  
  
SQL Server PDW は、ロックと同時実行制御を実装する、基になる SQL Server エンジンに依存します。 操作は、同じノード内の基になる SQL Server デッドロックにつながる、SQL Server PDW は、SQL Server のデッドロック検出の機能を活用し、ブロックのステートメントのいずれかを終了します。  
  
> [!NOTE]  
> SQL Server には、新しいロック要求がブロックされるまでにロックを待機しているステートメントはできません。 SQL Server PDW では、このプロセスは完全に実装がいません。 SQL Server PDW では、継続的なロックの要求を新しい共有は排他ロックの要求前 (ただし、待機中) の場合もありますブロックできます。 たとえば、**更新**(排他ロックを必要とする) ステートメントは、一連の許可されている共有ロックによってブロックされることができます**選択**ステートメントです。 ブロックされたプロセスを解決するのには (確認することで識別される、 [sys.dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md) DVM) 排他ロックが満たされているまで新しい要求の送信を停止してください。  
  
## <a name="lock-definition-table"></a>ロックの定義 テーブル  
SQL Server では、次の種類のロックをサポートします。 すべてのロックの種類は、コントロール ノードで利用できるが、コンピューティング ノードで発生する可能性があります。  
  
-   Sch-s (スキーマ安定度) です。 スキーマ エレメントに対してスキーマ安定度ロックが保持されているセッションの中では、テーブルやインデックスなどのスキーマ エレメントは削除されません。  
  
-   Sch-m (スキーマ修正)。 特定のリソースのスキーマを変更するセッションで保持される必要があります。 他のセッションで目的のオブジェクトが参照されないようにします。  
  
-   S (共有)。 保持しているセッションに、リソースへの共有アクセスが許可されます。  
  
-   U (更新) します。 リソース上で取得された更新ロックが、最終的に更新されることが許可されます。 これは、後で更新される可能性があるリソースが複数のセッションによってロックされるとき、一般的な形式のデッドロックが発生するのを防止するために使用します。  
  
-   X (排他)。 保持しているセッションで、リソースへの排他アクセスが許可されます。  
  
-   IS (インテント共有)。 ロック階層の下位のリソースに S ロックを設定するよう指定します。  
  
-   IU (更新インテント)。 ロック階層の下位のリソースに U ロックを設定するよう指定します。  
  
-   IX (排他インテント)。 ロック階層の下位のリソースに X ロックを設定するよう指定します。  
  
-   SIU (共有更新インテント)。 ロック階層の下位のリソースに更新ロックを設定する目的で、リソースへの共有アクセスを指定します。  
  
-   6 つ (共有排他インテント)。 ロック階層の下位のリソースに排他ロックを設定する目的で、リソースへの共有アクセスを指定します。  
  
-   UIX (更新排他インテント)。 ロック階層の下位のリソースに排他ロックを設定する目的で、リソースに保持する更新ロックを指定します。  
  
-   BU。 一括操作で使用します。  
  
-   RangeS_S (共有キー範囲と共有リソース ロック)。 直列化可能な範囲スキャンを指定します。  
  
-   RangeS_U (共有キー範囲と更新リソース ロック)。 直列化可能な更新スキャンを指定します。  
  
-   RangeI_N (挿入キー範囲と Null リソース ロック)。 新しいキーをインデックスに挿入する前に、範囲をテストするために使用します。  
  
-   RangeI_S です。 RangeI_N と S ロックの重なりによって作成されるキー範囲変換ロックです。  
  
-   範囲 I_u。 RangeI_N と U ロックの重なりによって作成されるキー範囲変換ロックです。  
  
-   範囲 I_x。 RangeI_N と X ロックの重なりによって作成されるキー範囲変換ロックです。  
  
-   RangeX_S です。 RangeI_N と RangeS_S ロックの重なりによって作成されるキー範囲変換 ロックです。  
  
-   RangeX_U です。 RangeI_N と RangeS_U ロックの重なりによって作成されるキー範囲変換ロックです。  
  
-   RangeX_X (排他キー範囲と排他リソース ロック)。 範囲内のキーを更新する場合に使用する変換ロックです。  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[sys.dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
