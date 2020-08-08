---
title: 移行されたデータベースオブジェクトのテスト (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f03ef5e1-66e6-4c84-ada2-252dd5ada82f
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 9e7c63986cde88c7a1ccbf67f8dd3751bb6d41b0
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87932833"
---
# <a name="testing-migrated-database-objects-oracletosql"></a>移行されたデータベース オブジェクトのテスト (OracleToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Oracle Tester (SSMA Tester) の Migration Assistant は、SSMA によって行われたデータベースオブジェクトの変換とデータ移行を自動的にテストします。 SSMA の移行手順がすべて完了したら、SSMA Tester を使用して、変換されたオブジェクトが同じように動作することと、すべてのデータが適切に転送されたことを確認します。  
  
SSMA Tester を使用して、次のオブジェクトの種類をテストできます。  
  
-   テーブル  
  
-   ストアドプロシージャ (パッケージプロシージャを含む)。  
  
-   ユーザー定義関数 (パッケージ化された関数を含む)。  
  
-   ビュー。  
  
-   スタンドアロンステートメント。  
  
SSMA Tester は、Oracle のテスト用に選択されたオブジェクトと、の対応するオブジェクトを実行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。 その後、次の条件に従って結果を比較します。  
  
-   テーブルデータの変更は同じですか。  
  
-   プロシージャと関数の出力パラメーターの値は同じですか。  
  
-   Do 関数は同じ結果を返しますか。  
  
-   結果セットが同一かどうか。  
  
> [!NOTE]  
> 注意 実稼働システムでは SSMA Tester を使用しないでください。 テスト担当者の実行中に、送信元スキーマとデータが変更されます。 一方、テスト対象のコードの種類によっては、元の状態を完全に復元できない場合があります。  
  
## <a name="prerequisites"></a>前提条件  
SSMA Tester を使用する場合は、[**テスト担当者データベースをインストール**する] オプションをオンにして Ssma Oracle Extension Pack をインストールします。  
  
結果のテーブルデータを比較できるようにするには、スキーマ変換が開始される前に [ **ROWID 列の生成**] オプションを **[はい]** に設定します。 SSMA は、[**スキーマの変換**] コマンドの実行中に、すべてのテーブルに ROWID 列を追加します。  
  
さらに、次のことを確認します。  
  
-   Oracle クライアントツールは、を実行するコンピューターにインストールされ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
-   データベースエンジンで共通言語ランタイム (CLR) 統合が有効になってい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
SSMA Tester の現在のバージョンでは、同じソースサーバーまたは対象サーバー上の異なるユーザーによる並列実行はサポートされていないことに注意してください。  
  
## <a name="getting-started"></a>はじめに  
[OracleToSQL&#41;&#40;のテストケースの作成](../../ssma/oracle/creating-test-cases-oracletosql.md)  
  
## <a name="see-also"></a>参照  
[SQL Server &#40;OracleToSQL&#41;での SSMA コンポーネントのインストール](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[プロジェクト設定 &#40;変換&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md)  
  
