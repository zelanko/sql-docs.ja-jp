---
title: 移行されたデータベースオブジェクトのテスト (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4937f6b4-86bd-4070-88df-3d216306c33a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 6fb469dfcaaec33a03681bfb64f411851df0400e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68020913"
---
# <a name="testing-migrated-database-objects-sybasetosql"></a>移行されたデータベース オブジェクトのテスト (SybaseToSQL)
Sybase Tester の Microsoft SQL Server Migration Assistant (SSMA Tester) は、データベースオブジェクトの変換と SSMA によって行われたデータの移行を自動的にテストします。 SSMA の移行手順がすべて完了したら、SSMA Tester を使用して、変換されたオブジェクトが同じように動作することと、すべてのデータが適切に転送されたことを確認します。  
  
> [!NOTE]  
> Azure 接続の場合、Tester コンポーネントは無効になっています。  
  
SSMA Tester を使用して、次のオブジェクトの種類をテストできます。  
  
-   テーブル  
  
-   ストアド プロシージャ  
  
-   ビュー。  
  
-   スタンドアロンステートメント。  
  
SSMA Tester は、Sybase のテスト用に選択されたオブジェクトと、SQL Server で対応するオブジェクトを実行します。 その後、次の条件に従って結果を比較します。  
  
-   テーブルデータの変更は同じですか。  
  
-   プロシージャと関数の出力パラメーターの値は同じですか。  
  
-   Do 関数は同じ結果を返しますか。  
  
-   結果セットが同一かどうか。  
  
> [!NOTE]  
> 気! 実稼働システムでは SSMA Tester を使用しないでください。 テスト担当者の実行中に、送信元スキーマとデータが変更されます。 一方、テスト対象のコードの種類によっては、元の状態を完全に復元できない場合があります。  
  
## <a name="prerequisites"></a>前提条件  
SSMA Tester を使用する場合は、[**テスト担当者データベースをインストール**する] オプションをオンにして Ssma Sybase Extension Pack をインストールします。  
  
さらに、次のことを確認します。  
  
-   を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]実行しているコンピューターに Sybase OLE DB プロバイダーがインストールされている。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースエンジンで共通言語ランタイム (CLR) 統合が有効になっています。  
  
SSMA Tester の現在のバージョンでは、同じソースサーバーまたは対象サーバー上の異なるユーザーによる並列実行はサポートされていないことに注意してください。  
  
## <a name="getting-started"></a>作業の開始  
[SybaseToSQL&#41;&#40;テストケースの作成](../../ssma/sybase/creating-test-cases-sybasetosql.md)  
  
## <a name="see-also"></a>参照  
[SSMA コンポーネントの SQL Server &#40;SybaseToSQL&#41;のインストール](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[プロジェクト設定 &#40;変換&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
