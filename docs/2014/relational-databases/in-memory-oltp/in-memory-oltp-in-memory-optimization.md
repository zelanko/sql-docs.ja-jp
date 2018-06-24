---
title: インメモリ OLTP (インメモリ最適化) | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- In-Memory OLTP
- memory-optimized tables
ms.assetid: e1d03d74-2572-4a55-afd6-7edf0bc28bdb
caps.latest.revision: 98
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: a7ee2a4a5a9bb56eee68aab349ff65ca811356cb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073300"
---
# <a name="in-memory-oltp-in-memory-optimization"></a>インメモリ OLTP (インメモリ最適化)
  [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]の新機能である [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] では、OLTP データベース アプリケーションのパフォーマンスを大幅に向上させることができます。 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エンジンに統合されたメモリ最適化データベース エンジンで、OLTP 用に最適化されています。  
  
|||  
|-|-|  
|![Azure の仮想マシン](../../master-data-services/media/azure-virtual-machine.png "Azure の仮想マシン")|SQL Server 2016 をお試しになりますか? Microsoft Azure にサインアップし、 **[ここ](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)** に移動して、SQL Server 2016 がインストール済みの仮想マシンを起動します。 完了後、仮想マシンは削除できます。|  
  
 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]を使用するには、頻繁にアクセスされるテーブルをメモリ最適化として定義します。 メモリ最適化テーブルは完全にトランザクション型であり、持続性があり、ディスク ベース テーブルと同じ方法で [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用してアクセスされます。 クエリでは、メモリ最適化テーブルとディスク ベース テーブルの両方を参照できます。 トランザクションでは、メモリ最適化テーブルおよびディスク ベース テーブル内のデータを更新できます。 メモリ最適化テーブルのみを参照するストアド プロシージャは、パフォーマンスをさらに向上させるために、マシン語コードにネイティブ コンパイルできます。 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] エンジンは、高度にスケールアウトされた中間層によって、OLTP タイプのトランザクションで発生する、非常に高いセッション同時実行性に対応するように設計されています。 このことを実現するために、ラッチ フリー データ構造と複数のバージョンから成るオプティミスティック同時実行制御が使用されます。 結果は、予測可能なミリ秒未満の低待機時間と、データベース トランザクションの線形スケールによる高いスループットです。 実際にパフォーマンスがどの程度向上するかは多くの要因によって異なりますが、一般的にはパフォーマンスが 5 ～ 20 倍向上します。  
  
 次の表に、 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]の使用によって最も大きい利点が得られるワークロード パターンを示します。  
  
|実装シナリオ|実装シナリオ|利点 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]|  
|-----------------------------|-----------------------------|-------------------------------------|  
|複数の同時接続からの高いデータ挿入レート|主に追加専用の格納<br /><br /> 挿入ワークロードに対する遅れ|競合の排除<br /><br /> ログ記録の削減|  
|読み取りパフォーマンスと、定期的な一括挿入および更新への対応|特に各サーバー要求で複数の読み取り操作が実行される場合の、パフォーマンスの高い読み取り操作<br /><br /> スケールアップ要件への対応不可|新しいデータが到着したときの競合の排除<br /><br /> 短い待機時間でのデータの取得<br /><br /> コードの実行時間の最小化|  
|データベース サーバーでのビジネス ロジックの集中処理|ワークロードの挿入、更新、および削除<br /><br /> ストアド プロシージャ内での集中計算<br /><br /> 読み取りと書き込みの競合|競合の排除<br /><br /> 待機時間の短縮とスループットの向上のためのコードの実行時間の最小化|  
|低待機時間|通常のデータベース ソリューションでは実現できない待機時間の短いビジネス トランザクションが必要|競合の排除<br /><br /> コードの実行時間の最小化<br /><br /> 待機時間の短いコード実行<br /><br /> 効率的なデータの取得|  
|セッション状態管理|頻繁な挿入、更新、およびポイント参照<br /><br /> 多数のステートレス Web サーバーからの高い負荷|競合の排除<br /><br /> 効率的なデータの取得<br /><br /> 持続性のないテーブルを使用する場合のオプションの IO 削減または削除|  
  
 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] によってパフォーマンスが大幅に向上するシナリオの詳細については、「 [インメモリ OLTP - 一般的なワークロード パターンと移行に関する考慮事項](http://msdn.microsoft.com/library/dn673538.aspx)」をご覧ください。  
  
 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] によって、特にトランザクションの実行時間が短い OLTP のパフォーマンスが向上します。  
  
 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] によって改善されるプログラミング パターンには、同時実行シナリオ、ポイント参照、大量の挿入と更新が行われる場合のワークロード、ストアド プロシージャのビジネス ロジックなどがあります。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と統合されているため、同じデータベースにメモリ最適化テーブルとディスク ベース テーブルの両方を保持し、両方の種類のテーブルをまたいでクエリを実行することもできます。  
  
 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] では、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] に関してサポートされる [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]の対象領域に制限があります。  
  
 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 使用してパフォーマンスとスケーラビリティの大幅な向上を実現します。  
  
-   メモリ常駐のデータへのアクセスに最適化されたアルゴリズム。  
  
-   論理ロックが不要なオプティミスティック同時実行制御。  
  
-   物理的なロックおよびラッチをすべて排除するロックフリーのオブジェクト。 トランザクション操作を実行するスレッドでは、同時実行制御のためにロックやラッチは使用されません。  
  
-   ネイティブ コンパイル ストアド プロシージャ。メモリ最適化テーブルにアクセスする場合に、解釈されたストアド プロシージャよりもパフォーマンスは大幅に向上します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]を使用するためには、テーブルやストアド プロシージャの構文の変更が必要になることがあります。 詳細については、「[インメモリ OLTP への移行](migrating-to-in-memory-oltp.md)」を参照してください。 ディスク ベース テーブルをメモリ最適化テーブルに移行する前に、「[テーブルまたはストアド プロシージャをインメモリ OLTP に移植する必要があるかどうかの確認](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)」を参照して、[!INCLUDE[hek_2](../../../includes/hek-2-md.md)] の利点を受けることができるテーブルとストアド プロシージャをご確認ください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 このセクションでは、以下の概念について説明します。  
  
|トピック|説明|  
|-----------|-----------------|  
|[メモリ最適化テーブルを使用するための要件](memory-optimized-tables.md)|メモリ最適化テーブルを使用するためのハードウェア要件、ソフトウェア要件、およびガイドラインについて説明します。|  
|[VM 環境でのインメモリ OLTP の使用](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)|仮想化環境での [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] の使用について説明します。|  
|[インメモリ OLTP のコード サンプル](in-memory-oltp-code-samples.md)|メモリ最適化テーブルを作成して使用する方法を示すコード例が記載されています。|  
|[メモリ最適化テーブル](memory-optimized-tables.md)|メモリ最適化テーブルの概要を示します。|  
|[メモリ最適化テーブル変数](../../database-engine/memory-optimized-table-variables.md)|tempdb の使用を減らすために、従来のテーブル変数の代わりにメモリ最適化テーブル変数を使用する方法を示すコード例です。|  
|[メモリ最適化テーブルのインデックス](../../database-engine/indexes-on-memory-optimized-tables.md)|メモリ最適化インデックスを示します。|  
|[ネイティブ コンパイル ストアド プロシージャ](natively-compiled-stored-procedures.md)|ネイティブ コンパイル ストアド プロシージャについて説明します。|  
|[インメモリ OLTP のメモリ管理](../../database-engine/managing-memory-for-in-memory-oltp.md)|システムのメモリ使用量について説明し、メモリ使用量を管理する方法を示します。|  
|[メモリ最適化オブジェクト用ストレージの作成と管理](creating-and-managing-storage-for-memory-optimized-objects.md)|メモリ最適化テーブルでのトランザクションに関する情報を格納するデータ ファイルとデルタ ファイルについて説明します。|  
|[メモリ最適化テーブルのバックアップ、復元、復旧](restore-and-recovery-of-memory-optimized-tables.md)|メモリ最適化テーブルのバックアップ、復元、および復旧について説明します。|  
|[Transact-SQL によるインメモリ OLTP のサポート](transact-sql-support-for-in-memory-oltp.md)|[!INCLUDE[tsql](../../../includes/tsql-md.md)] による [!INCLUDE[hek_2](../../../includes/hek-2-md.md)]のサポートについて説明します。|  
|[インメモリ OLTP データベースにおける高可用性のサポート](high-availability-support-for-in-memory-oltp-databases.md)|[!INCLUDE[hek_2](../../../includes/hek-2-md.md)]での可用性グループおよびフェールオーバー クラスタリングについて説明します。|  
|[SQL Server によるインメモリ OLTP のサポート](sql-server-support-for-in-memory-oltp.md)|新しい構文および機能、更新された構文および機能のうち、メモリ最適化テーブルをサポートするものを一覧にして紹介します。|  
|[インメモリ OLTP への移行](migrating-to-in-memory-oltp.md)|ディスク ベース テーブルをメモリ最適化テーブルに移行する方法について説明します。|  
  
 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] の詳細な情報は、以下で参照できます。  
  
-   [Microsoft® SQL Server® 2014 製品ガイド](http://www.microsoft.com/download/confirmation.aspx?id=39269)  
  
-   [インメモリ OLTP ブログ](http://go.microsoft.com/fwlink/?LinkId=311696)  
  
-   [インメモリ OLTP - 一般的なワークロード パターンと移行に関する考慮事項](http://msdn.microsoft.com/library/dn673538.aspx)  
  
-   [SQL Server インメモリ OLTP 内部概要](http://msdn.microsoft.com/library/dn720242.aspx)  
  
## <a name="see-also"></a>参照  
 [データベース機能](../database-features.md)  
  
  