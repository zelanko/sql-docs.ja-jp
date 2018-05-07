---
title: SQL Server 機能の OLE DB Driver |Microsoft ドキュメント
description: OLE DB ドライバーの SQL Server 機能
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], features
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 3f1cc26981dae02bd76133c204c5eff142db76c5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-driver-for-sql-server-features"></a>SQL Server 機能の OLE DB ドライバー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Windows (以前の Microsoft) Data Access Components (WDAC) の機能を公開するだけでなく OLE DB Driver for SQL Server もを実装するその他の多くの機能を公開する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]機能します。  
  
## <a name="in-this-section"></a>このセクションの内容    
 [データベース ミラーリングの使用](../../oledb/features/using-database-mirroring.md)  
 OLE DB Driver for SQL Server でのコピー、およびミラーを保持することが、ミラー化されたデータベースの使用をサポートする方法について説明します、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]スタンバイ サーバー上のデータベースです。  
  
 [非同期操作の実行](../../oledb/features/performing-asynchronous-operations.md)  
 OLE DB Driver for SQL Server でサポートする方法、非同期操作の呼び出し元のスレッドをブロックせずにすぐに戻るにことがについて説明します。  
  
 [複数のアクティブな結果セット &#40;MARS&#41; の使用](../../oledb/features/using-multiple-active-result-sets-mars.md)  
 OLE DB Driver for SQL Server で複数のアクティブな結果セット (MARS) をサポートする方法について説明します。 MARS では、単一のデータベース接続を使用して、複数の結果セットを実行したり受け取ったりできます。  
  
 [XML データ型の使用](../../oledb/features/using-xml-data-types.md)  
 OLE DB Driver for SQL Server では、XML ベースのデータ型列の型、変数の型、パラメーターの型、または関数の戻り値の型として使用できる XML データ型をサポートする方法について説明します。  
  
 [ユーザー定義型の使用](../../oledb/features/using-user-defined-types.md)  
 OLE DB Driver for SQL Server でユーザー定義型 (UDT)、オブジェクトやカスタム データ構造を格納することにより、SQL 型システムを拡張するものをサポートする方法について説明します、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベース。  
  
 [大きな値の型を使用します。](../../oledb/features/using-large-value-types.md)  
 OLE DB Driver for SQL Server ではラージ オブジェクト (LOB) データ型、大きな値データ型をサポートする方法について説明します。  
  
 [プログラムによるパスワードの変更](../../oledb/features/changing-passwords-programmatically.md)  
 OLE DB Driver for SQL Server に期限切れのパスワードの処理がサポートされているため、パスワードを変更できるように管理者の関与なしでクライアントにする方法について説明します。  
  
 [スナップショット分離の使用](../../oledb/features/working-with-snapshot-isolation.md)  
 OLE DB Driver for SQL Server でリーダー/ライターのブロッキング問題を回避することでデータベースのパフォーマンスを向上させる行のバージョン管理の拡張機能をサポートする方法について説明します。  
  
 [クエリ通知の操作](../../oledb/features/working-with-query-notifications.md)  
 OLE DB Driver for SQL Server でコンシューマーに通知をサポートする、行セットの変更の方法について説明します。  
  
 [一括コピー操作の実行](../../oledb/features/performing-bulk-copy-operations.md)  
 OLE DB Driver for SQL Server での大量のデータの転送を許可する一括コピー操作をサポートする方法について説明します、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブルまたはビュー。  
  
 [検証を伴わない暗号化の使用](../../oledb/features/using-encryption-without-validation.md)  
 OLE DB Driver for SQL Server を使用して、証明書を検証せず、サーバーに送信されるデータを暗号化する方法について説明します。  
  
 [テーブル値パラメーター &#40;OLE DB Driver for SQL Server&#41;](../../oledb/features/table-valued-parameters-oledb-driver-for-sql-server.md)  
 テーブル値パラメーターの SQL Server のサポートについては、OLE DB ドライバーを説明します。  
  
 [大きな CLR ユーザー定義型](../../oledb/features/large-clr-user-defined-types.md)  
 大きな共通言語ランタイム (CLR) ユーザー定義型 (UDT) のサポートについて説明します。  
  
 [FILESTREAM のサポート](../../oledb/features/filestream-support.md)  
 SQL Server のサポート、強化された FILESTREAM 機能の OLE DB Driver について説明します。  
  
 [サービス プリンシパル名&#40;SPN&#41;クライアント接続でのサポート](../../oledb/features/service-principal-name-spn-support-in-client-connections.md)  
 あらゆるプロトコルでの相互認証を可能にする、サービス プリンシパル名 (SPN) のサポート強化について説明します。  
  
 [OLE DB Driver for SQL Server のスパース列のサポート](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md)  
 スパース列の SQL Server のサポートについては、OLE DB ドライバーを説明します。  
  
 [日付と時刻の強化機能](../../oledb/features/date-and-time-improvements.md)  
 日付と時刻のデータ型の SQL Server の OLE DB ドライバーに追加のサポートについて説明します。  
  
 [メタデータの検出](../../oledb/features/metadata-discovery.md)  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] で行われたメタデータ検出の機能強化について説明します。  
  
 [OLE DB Driver for SQL Server の UTF-16 のサポート](../../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] で導入された動作の変更について説明します。 列の結果または出力パラメーターをバインドするときに、固定長バッファーを指定した場合、 **wchar**終端文字がサロゲート ペアの上位サロゲート コード ポイントする前に、バッファーに書き込まれた文字、次へ**wchar**文字が下位サロゲート コード ポイントで、OLE DB Driver for SQL Server は、バッファーに上位サロゲート コード ポイントを追加しません。  
  
 [OLE DB Driver for SQL Server の高可用性、ディザスター リカバリーに関するサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  
 機能が追加された高可用性、災害復旧を活用するために、アプリケーションを構成する方法について説明[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]です。  
  
 [拡張イベント ログの診断情報へのアクセス](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  
 OLE DB Driver for SQL Server とリング バッファーおよび Xevent ログの診断情報にアクセスできるデータ トレース機能強化について説明します。  
  
 [LocalDB 用 OLE DB Driver for SQL Server のサポート](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  
 SQL Server LocalDB 機能のサポートの OLE DB Driver について説明します。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server](../../oledb/oledb-driver-for-sql-server.md)      
 [OLE DB の操作方法に関するトピック](../../oledb/ole-db-how-to/ole-db-how-to-topics.md)   
 [OLE DB Driver for SQL Server のインストール](../../oledb/applications/installing-oledb-driver-for-sql-server.md)  
  
  
