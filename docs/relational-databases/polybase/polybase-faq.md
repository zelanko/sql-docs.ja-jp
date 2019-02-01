---
title: PolyBase のよく寄せられる質問 |Microsoft Docs
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: ''
ms.openlocfilehash: 331ac177831b1e07cfab253c363a35f2bab42a6c
ms.sourcegitcommit: ee76381cfb1c16e0a063315c9c7005f10e98cfe6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2019
ms.locfileid: "55072880"
---
# <a name="frequently-asked-questions"></a>よく寄せられる質問

## <a name="polybase-in-big-data-clusters-vs-polybase-in-stand-alone-instances"></a>ビッグ データ クラスターの PolyBase と スタンドアロン インスタンスの PolyBase

|機能 |ビッグ データ クラスター| スタンドアロン インスタンス|
|--------------------------|--------------------------|---------|   
|外部テーブルを作成する| ×| ×|
|SQL Server、Oracle、Teradata、および Mongo DB から外部データ ソースを作成する |×|× |
|互換性のあるサードパーティ製 ODBC ドライバーを使用して外部データ ソースを作成する | | ×|
|PolyBase スケールアウト グループ | × | |
|データ プール インスタンス | ×| |
|ストレージ プール インスタンス| ×| |

>[!NOTE]
>
>ODBC ジェネリック コネクタを使用した接続の詳細については、「[How-to guide for configuring ODBC generic types](polybase-configure-odbc-generic.md)」(ODBC ジェネリック型を構成するためのハウツー ガイド) を参照してください。

## <a name="whats-new-with-polybase-in-sql-server-2019"></a>SQL Server 2019 の PolyBase の新機能 

SQL Server 2019 の PolyBase は、さまざまな大規模なデータ ソースからデータを読み取ることができるようになりました。 これらの外部データ ソースのデータは、SQL Server で外部テーブルとして保存できます。 PolyBase では、ODBC ジェネリック型を除くこれらの外部データ ソースへのプッシュ ダウン計算もサポートします。 

### <a name="compatible-data-sources"></a>互換性のあるデータ ソース

- SQL Server
- Oracle
- Teradata
- MongoDB
- **互換性のある** ODBC ジェネリック型

  > [!NOTE]
  >
  >PolyBase では、サード パーティ製 ODBC ドライバーを使用して外部データ ソースへの接続を許可できます。 これらのドライバーは PolyBase と共に提供されておらず、意図したとおりに動作する可能性があります。 詳細については、PolyBase ODBC ジェネリック構成に関する[ガイド](polybase-configure-odbc-generic.md)を参照してください。  

## <a name="polybase-vs-linked-servers"></a>PolyBase と リンク サーバー

|PolyBase | リンク サーバー|
|--------------------------|--------------------------|  
|データベース スコープ オブジェクト|インスタンス スコープ オブジェクト| 
|ODBC ドライバーを使用します|OLEDB プロバイダーを使用します| 
| 読み取り専用操作のみをサポートします。 今後拡張されます| 読み取り専用操作のみをサポートします。 今後拡張されます| 
|クエリはスケールアウト可能で、プッシュダウンがサポートされています|クエリはシングルスレッドで、プッシュダウンがサポートされています|
|Always On 可用性グループに必要な個別の構成はありません|Always On 可用性グループの各インスタンスに個別の構成が必要です|
|基本認証のみ。 SQL Server 2019 の改良|基本認証と統合認証|