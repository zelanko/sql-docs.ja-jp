---
title: ディスク ベース テーブル ストレージとメモリ最適化テーブル ストレージの比較
description: ディスクベースとメモリ最適化テーブルのストレージを、DDL、構造体、インデックス、DML 操作、データの断片化のカテゴリで比較します。
ms.custom: seo-dt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: eacf443c-001a-445f-ad1c-5f5a45eca6f4
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f2539dfdb2ccd72516e69daeb1c6833727c2e1f8
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542917"
---
# <a name="comparing-disk-based-table-storage-to-memory-optimized-table-storage"></a>ディスク ベース テーブル ストレージとメモリ最適化テーブル ストレージの比較
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  
  
|Categories|ディスク ベース テーブル|持続性のあるメモリ最適化テーブル|  
|----------------|-----------------------|-------------------------------------|  
|DDL (DDL)|メタデータ情報は、データベースのプライマリ ファイル グループのシステム テーブルに格納され、カタログ ビューを使用してアクセスできます。|メタデータ情報は、データベースのプライマリ ファイル グループのシステム テーブルに格納され、カタログ ビューを使用してアクセスできます。|  
|構造体|行は 8 KB 単位のページに格納されます。 1 ページには同じテーブルの行だけが格納されます。|行は個別の行として格納されます。 ページ構造はありません。 データ ファイル内の連続する 2 行はそれぞれ別のメモリ最適化テーブルに属することができます。|  
|インデックス|インデックスは、データ行と同様のページ構造に格納されます。|(インデックス行ではなく) インデックス定義のみが保存されます。 インデックスはメモリ内に保持され、データベース再起動の一部としてメモリ最適化テーブルがメモリに読み込まれるときに再生成されます。 インデックス行は持続しないので、インデックスの変更に対してログ記録は実行されません。|  
|DML 操作|最初の手順は、ページを見つけてバッファー プールに読み込むことです。<br /><br /> 挿入<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、クラスター化インデックスの場合に行の順序を考慮して、ページ上に行を挿入します。<br /><br /> 削除<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、ページ上の削除する行を検索し、削除のマークを付けます。<br /><br /> 更新<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、ページ上の行を検索します。 更新は非キー列に対してインプレースで実行されます。 キー列の更新は削除と挿入操作によって実行されます。<br /><br /> DML 操作の完了後、影響を受けるページは、最小ログ記録操作に関するバッファー プール ポリシー、チェックポイント、またはトランザクションのコミットの一部としてディスクにフラッシュされます。 ページに対する読み取り/書き込みの両方が不要な I/O につながります。|メモリ最適化テーブルの場合、データがメモリに格納されるので、DML 操作はメモリ内で直接実行されます。 メモリ最適化テーブルのログ レコードを読み取ってデータ ファイルとデルタ ファイルに保存するバックグラウンド スレッドがあります。 更新では新しい行バージョンが生成されます。 ただし、更新は削除としてログに記録され、その後に挿入が続きます。|  
|データの断片化|データ操作のフラグメント データにより、一部分しか入力されていないページや、ディスクでは連続していない論理的に連続するページが生じる可能性があります。 これにより、データ アクセスのパフォーマンスが低下するため、データのデフラグが必要になります。|メモリ最適化データはページに格納されないので、データの断片化はありません。 ただし、行が更新または削除されると、データ ファイルとデルタ ファイルは圧縮が必要になります。 これは、マージ ポリシーに基づいて、バックグラウンドの MERGE スレッドで実行されます。|  
  
## <a name="see-also"></a>参照  
 [メモリ最適化オブジェクト用ストレージの作成と管理](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
