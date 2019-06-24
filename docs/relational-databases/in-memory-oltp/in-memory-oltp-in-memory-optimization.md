---
title: インメモリ OLTP (インメモリ最適化) | Microsoft Docs
ms.custom: ''
ms.date: 11/22/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- In-Memory OLTP
- memory-optimized tables
ms.assetid: e1d03d74-2572-4a55-afd6-7edf0bc28bdb
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d5d982ba0b7a2ec5b35a6d38da3a5831119c4c1c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63047576"
---
# <a name="in-memory-oltp-in-memory-optimization"></a>インメモリ OLTP (インメモリ最適化)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] は、トランザクション処理、データの取り込み、データの読み込みのパフォーマンス、および一時的なデータのシナリオを大幅に向上させることができます。  独自のメモリ最適化テーブルとネイティブ コンパイル ストアド プロシージャをすばやくテストするために必要な基本的なコードと知識については、
 -  [クイック スタート 1:Transact-SQL のパフォーマンスを向上させるインメモリ OLTP テクノロジ](../../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md)」を参照してください。  
 
インメモリ OLTP について説明し、パフォーマンス上の利点を示す 17 分の動画:

-  [In-Memory OLTP in SQL Server 2016](https://www.youtube.com/watch?v=l5l5eophmK4)(SQL Server 2016 のインメモリ OLTP)

動画で使用されているインメモリ OLTP のパフォーマンス デモをダウンロードするには: 

- [インメモリ OLTP パフォーマンス デモ v1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0)

インメモリ OLTP の詳細な概要、およびテクノロジからパフォーマンスの利点を享受するシナリオのレビュー:

- [概要と使用シナリオ](../../relational-databases/in-memory-oltp/overview-and-usage-scenarios.md)
 
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] は、トランザクション処理のパフォーマンスを向上させる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テクノロジであることに注意してください。 報告と分析クエリのパフォーマンスを向上させる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テクノロジについては、「 [列ストア インデックスの説明](../../relational-databases/indexes/columnstore-indexes-overview.md)」を参照してください。
  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]、[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]、および [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] では、インメモリ OLTP はいくつかの機能強化が行われています。 データベース アプリケーションの移行を容易にできるように、Transact-SQL の表層が拡大されています。 アプリケーションのメンテナンスを容易にできるように、メモリ最適化テーブルとネイティブ コンパイル ストアド プロシージャの ALTER 操作を実行するためのサポートが追加されています。 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] の新機能については、「[Columnstore indexes - what's new](../../relational-databases/indexes/columnstore-indexes-what-s-new.md)」(Columnstore インデックス - 新機能) を参照してください。  
  
> [!NOTE]  
>  **お試しください**  
>   
>  インメモリ OLTP は、Premium および Business Critical 層の Azure SQL Database およびエラスティック プールで使用できます。 インメモリ OLTP および Azure SQL Database の列ストアの使用を開始するには、「 [SQL Database でのインメモリ (プレビュー) の使用](https://azure.microsoft.com/documentation/articles/sql-database-in-memory/)」をご覧ください。  
  

## <a name="in-this-section"></a>このセクションの内容  
 このセクションの内容は次のとおりです。  
  
|トピック|[説明]|  
|-----------|-----------------|  
|[クイック スタート 1:Transact-SQL のパフォーマンスを向上させるインメモリ OLTP テクノロジ](../../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md)|インメモリ OLTP について深く掘り下げて考えます|
|[概要と使用シナリオ](../../relational-databases/in-memory-oltp/overview-and-usage-scenarios.md)|インメモリ OLTP の内容、およびパフォーマンス上の利点を活用するシナリオの概要です。|
|[メモリ最適化テーブルを使用するための要件](../../relational-databases/in-memory-oltp/requirements-for-using-memory-optimized-tables.md)|メモリ最適化テーブルを使用するためのハードウェア要件、ソフトウェア要件、およびガイドラインについて説明します。|  
|[インメモリ OLTP のコード サンプル](../../relational-databases/in-memory-oltp/in-memory-oltp-code-samples.md)|メモリ最適化テーブルを作成して使用する方法を示すコード例が記載されています。|  
|[メモリ最適化テーブル](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)|メモリ最適化テーブルの概要を示します。|  
|[メモリ最適化テーブル変数](https://msdn.microsoft.com/library/bd102e95-53e2-4da6-9b8b-0e4f02d286d3)|tempdb の使用を減らすために、従来のテーブル変数の代わりにメモリ最適化テーブル変数を使用する方法を示すコード例です。|  
|[メモリ最適化テーブルのインデックス](https://msdn.microsoft.com/library/86805eeb-6972-45d8-8369-16ededc535c7)|メモリ最適化インデックスを示します。|  
|[ネイティブ コンパイル ストアド プロシージャ](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)|ネイティブ コンパイル ストアド プロシージャについて説明します。|  
|[インメモリ OLTP のメモリ管理](https://msdn.microsoft.com/library/d82f21fa-6be1-4723-a72e-f2526fafd1b6)|システムのメモリ使用量について説明し、メモリ使用量を管理する方法を示します。|  
|[メモリ最適化オブジェクト用ストレージの作成と管理](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)|メモリ最適化テーブルでのトランザクションに関する情報を格納するデータ ファイルとデルタ ファイルについて説明します。|  
|[メモリ最適化テーブルのバックアップ、復元、復旧](https://msdn.microsoft.com/library/3f083347-0fbb-4b19-a6fb-1818d545e281)|メモリ最適化テーブルのバックアップ、復元、および復旧について説明します。|  
|[Transact-SQL によるインメモリ OLTP のサポート](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)|[!INCLUDE[tsql](../../includes/tsql-md.md)] による [!INCLUDE[hek_2](../../includes/hek-2-md.md)]のサポートについて説明します。|  
|[インメモリ OLTP データベースにおける高可用性のサポート](../../relational-databases/in-memory-oltp/high-availability-support-for-in-memory-oltp-databases.md)|[!INCLUDE[hek_2](../../includes/hek-2-md.md)]での可用性グループおよびフェールオーバー クラスタリングについて説明します。|  
|[SQL Server によるインメモリ OLTP のサポート](../../relational-databases/in-memory-oltp/sql-server-support-for-in-memory-oltp.md)|新しい構文および機能、更新された構文および機能のうち、メモリ最適化テーブルをサポートするものを一覧にして紹介します。|  
|[インメモリ OLTP への移行](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)|ディスク ベース テーブルをメモリ最適化テーブルに移行する方法について説明します。|  
  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] の詳細な情報は、以下で参照できます。  

- [インメモリ OLTP について説明し、パフォーマンス上の利点を示す動画](https://www.youtube.com/watch?v=l5l5eophmK4)

- [インメモリ OLTP パフォーマンス デモ v1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0)

-   [SQL Server インメモリ OLTP 内部技術ホワイト ペーパー](https://msdn.microsoft.com/library/mt764316.aspx)  

-   [SQL Server のインメモリ OLTP と列ストア機能の比較](https://download.microsoft.com/download/D/0/0/D0075580-6D72-403D-8B4D-C3BD88D58CE4/SQL_Server_2016_In_Memory_OLTP_and_Columnstore_Comparison_White_Paper.pdf)

-   SQL Server 2016 のインメモリ OLTP の新機能の [第 1 部](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/11/12/in-memory-oltp-whats-new-in-sql2016-ctp3/) と [第 2 部](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/25/whats-new-for-in-memory-oltp-in-sql-server-2016-since-ctp3/)
  
-   [インメモリ OLTP - 一般的なワークロード パターンと移行に関する考慮事項](https://msdn.microsoft.com/library/dn673538.aspx)  
  
-   [インメモリ OLTP ブログ](https://go.microsoft.com/fwlink/?LinkId=311696)  
  
## <a name="see-also"></a>参照  
 [データベース機能](../../relational-databases/database-features.md)  
  
  
