---
title: ロック動作の Parallel Data Warehouse |Microsoft Docs
description: Parallel Data Warehouse との使用方法のロック トランザクションの整合性を確保する複数のユーザーが同時にデータにアクセスするときに、データベースの一貫性を維持するために説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d93743c83d6315e6ab9484445f344b06f80be845
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960642"
---
# <a name="locking-behavior-in-parallel-data-warehouse"></a>Parallel Data Warehouse でのロック動作
Parallel Data Warehouse との使用方法のロック トランザクションの整合性を確保する複数のユーザーが同時にデータにアクセスするときに、データベースの一貫性を維持するために説明します。  
  
## <a name="Basics"></a>ロックの基礎  
**モード**  
  
SQL Server PDW では、4 つのロック モードがサポートされています。  
  
[Exclusive]  
排他ロックへの書き込みや、トランザクションが完了すると、排他ロックを保持するまでロックされたオブジェクトからの読み取りを禁止します。 排他ロックが有効なときにその他のロックを任意のモードは許可されません。 たとえば、DROP TABLE、CREATE DATABASE は、排他ロックを使用します。  
  
Shared  
共有ロックは、影響を受けるオブジェクトの排他ロックの開始に使用が禁止されていますが、他のすべてのロック モードを許可します。 たとえば、SELECT ステートメント、共有ロックを開始しますしたがって複数のクエリを同時に、選択したデータにアクセスできますが、SELECT ステートメントが完了するまでは、読み取られるレコードの更新を回避します。  
  
ExclusiveUpdate  
ExclusiveUpdate ロックはロックされたオブジェクトへの書き込みを禁止されていますが、共有ロックを使用して読み取りを許可するが。 ExclusiveUpdate ロックが有効なときに、他のロックを許可されません。 たとえば、データベースのバックアップと復元のデータベースは、排他的更新ロックを使用します。  
  
SharedUpdate  
Exclusive および ExclusiveUpdate ロック モードと共有] および [SharedUpdate ロック モードでは、オブジェクト上 SharedUpdate ロック。 SharedUpdate は、オブジェクトを変更しますが、変更中に読み取りアクセスは制限されません。 たとえば、挿入し、更新での SharedUpdate ロックを使用します。  
  
**リソース クラス**  
  
オブジェクトの次のクラスで、ロックが保持されます。データベース、スキーマ、オブジェクト (テーブル、ビュー、またはプロシージャ)、(内部的に使用される) アプリケーション、EXTERNALDATASOURCE、EXTERNALFILEFORMAT および SCHEMARESOLUTION (データベース レベルのロックを作成、変更、またはスキーマ オブジェクトまたはデータベース ユーザーを削除中に実行された)。 これらのオブジェクト クラスは、の object_type 列に表示できる[sys.dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)します。  
  
## <a name="Remarks"></a>全般的な解説  
ロックは、データベース、テーブル、またはビューに適用できます。  
  
SQL Server PDW は、構成可能な分離レベルを実装していません。 ANSI 標準で定義されている READ_UNCOMMITTED 分離レベルをサポートします。 ただし、READ_UNCOMMITTED で操作が実行される読み取り、非常にいくつかのブロック操作実際に発生する、またはシステムでの競合をリードです。  
  
SQL Server PDW は、ロックと同時実行制御を実装する、基になる SQL Server エンジンに依存します。 操作は、同じノード内の基になる SQL Server デッドロックにつながる、SQL Server PDW は、SQL Server のデッドロック検出機能を活用し、ブロックのステートメントのいずれかを終了します。  
  
> [!NOTE]  
> SQL Server では、ロック新しいロック要求によってブロックされるを待機しているステートメントは許可されません。 SQL Server PDW では、このプロセスは完全に実装がいません。 SQL Server PDW では、新しい共有ロックの継続的な要求は排他ロックの要求を前 (ただし、待機している) 場合がありますをブロックできます。 たとえば、 **UPDATE** (排他ロックを必要とする) ステートメントは、一連の与えられている共有ロックによってブロックされることができます**選択**ステートメント。 ブロックされたプロセスを解決するのには (レビューで識別される、 [sys.dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md) DVM) を排他ロックが満たされているまで新しい要求の送信を停止します。  
  
## <a name="lock-definition-table"></a>定義のテーブルをロック  
SQL Server では、次の種類のロックをサポートします。 すべてロックの種類は、制御ノードで使用可能ながコンピューティング ノードで発生する可能性があります。  
  
-   Sch-s (スキーマ安定度)。 スキーマ エレメントに対してスキーマ安定度ロックが保持されているセッションの中では、テーブルやインデックスなどのスキーマ エレメントは削除されません。  
  
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
  
-   RangeI_S します。 RangeI_N と S ロックの重なりによって作成されるキー範囲変換ロックです。  
  
-   I_u。 RangeI_N と U ロックの重なりによって作成されるキー範囲変換ロックです。  
  
-   I_x。 RangeI_N と X ロックの重なりによって作成されるキー範囲変換ロックです。  
  
-   RangeX_S します。 RangeI_N と RangeS_S ロックの重なりによって作成されるキー範囲変換 ロックです。  
  
-   RangeX_U します。 RangeI_N と RangeS_U ロックの重なりによって作成されるキー範囲変換ロックです。  
  
-   RangeX_X (排他キー範囲と排他リソース ロック)。 範囲内のキーを更新する場合に使用する変換ロックです。  
  
## <a name="see-also"></a>関連項目  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[sys.dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
